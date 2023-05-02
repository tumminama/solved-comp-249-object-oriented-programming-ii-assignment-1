Download Link: https://assignmentchef.com/product/solved-comp-249-object-oriented-programming-ii-assignment-1
<br>
<strong>Purpose:</strong>The purpose of this assignment is to help you practice/review arrays of objects and objet oriented design.

<strong> </strong>

<h1>Battleship</h1>

<strong> </strong>In this assignment, you will write a program to play a game of Battleship against the computer.  Our simplified version of the game will be played on a single 8 by 8 grid.  Before the actual game, each player secretly places 6 ships and 4 grenades on the grid.  Ships and grenades are a single position on the grid. The position of these ships and grenades are of course hidden from the opponent.  Once both players have placed their ships and grenades, the actual game starts.  Each player, in turn, “shoots a rocket” on the grid (i.e. calls a position).

<ul>

 <li>If the rocket (the position called) falls on a position where there is nothing, then nothing happens, and the other player can shoot his/her rocket.</li>

 <li>If the rocket falls on a coordinate where the opponent (or the player) has a grenade, then the player loses a turn, and next time, the opponent will play twice in a row. You will need to keep track of the total number of missed turns due to that and display that number once the game has ended.</li>

 <li>If the rocket falls on a coordinate where the opponent (or the player…) has a ship, then that ship sinks.</li>

 <li>If the rocket falls on a coordinate that has been called before, regardless of what was there before, nothing happens. (So for example, a grenade can only explode once).</li>

</ul>




The goal of the game is to sink all of your opponent’s ships before your opponent sinks yours.




For the sake of simplicity, you can assume that ships and grenades cannot overlap.  So you cannot have 2 grenades on the same position, have 2 ships on the same position, or have a grenade on a ship.




For example, let’s consider the following grid:

<table width="201">

 <tbody>

  <tr>

   <td width="27"></td>

   <td width="22">A</td>

   <td width="22">B</td>

   <td width="22">C</td>

   <td width="22">D</td>

   <td width="22">E</td>

   <td width="22">F</td>

   <td width="22">G</td>

   <td width="22">H</td>

  </tr>

  <tr>

   <td width="27">1</td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">G</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">S</td>

   <td width="22">g</td>

  </tr>

  <tr>

   <td width="27">2</td>

   <td width="22"></td>

   <td width="22">g</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

  </tr>

  <tr>

   <td width="27">3</td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

  <tr>

   <td width="27">4</td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">S</td>

   <td width="22">s</td>

  </tr>

  <tr>

   <td width="27">5</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

  <tr>

   <td width="27">6</td>

   <td width="22">S</td>

   <td width="22">G</td>

   <td width="22">g</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">G</td>

  </tr>

  <tr>

   <td width="27">7</td>

   <td width="22"></td>

   <td width="22">G</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">g</td>

  </tr>

  <tr>

   <td width="27">8</td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

 </tbody>

</table>

<strong> </strong>

Here, one player (identified in black) has his/her 6 ships at positions A1, G1, A4, C4, G4 and A6 and 4 grenades at positions D1, B6, B7 and H6.  The other player has his/her ships at H2, A3, E3, H4, E5 and C8 and 4 grenades at positions H1, B2, C6 and H7.




If black starts the game and “shoots a rocket” at position D2 then nothing happens, and we have the following grid.

<table width="201">

 <tbody>

  <tr>

   <td width="27"></td>

   <td width="22">A</td>

   <td width="22">B</td>

   <td width="22">C</td>

   <td width="22">D</td>

   <td width="22">E</td>

   <td width="22">F</td>

   <td width="22">G</td>

   <td width="22">H</td>

  </tr>

  <tr>

   <td width="27">1</td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">G</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">S</td>

   <td width="22">g</td>

  </tr>

  <tr>

   <td width="27">2</td>

   <td width="22"></td>

   <td width="22">g</td>

   <td width="22"></td>

   <td width="22">*</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

  </tr>

  <tr>

   <td width="27">3</td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

  <tr>

   <td width="27">4</td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">S</td>

   <td width="22">s</td>

  </tr>

  <tr>

   <td width="27">5</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

  <tr>

   <td width="27">6</td>

   <td width="22">S</td>

   <td width="22">G</td>

   <td width="22">g</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">G</td>

  </tr>

  <tr>

   <td width="27">7</td>

   <td width="22"></td>

   <td width="22">G</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">g</td>

  </tr>

  <tr>

   <td width="27">8</td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

 </tbody>

</table>













It is white’s turn now.  White shoots at G4. The rocket hits one of black’s ship.  The ship sinks.  We now have:

<table width="201">

 <tbody>

  <tr>

   <td width="27"></td>

   <td width="22">A</td>

   <td width="22">B</td>

   <td width="22">C</td>

   <td width="22">D</td>

   <td width="22">E</td>

   <td width="22">F</td>

   <td width="22">G</td>

   <td width="22">H</td>

  </tr>

  <tr>

   <td width="27">1</td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">G</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">S</td>

   <td width="22">g</td>

  </tr>

  <tr>

   <td width="27">2</td>

   <td width="22"></td>

   <td width="22">g</td>

   <td width="22"></td>

   <td width="22">*</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

  </tr>

  <tr>

   <td width="27">3</td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

  <tr>

   <td width="27">4</td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">*</td>

   <td width="22">s</td>

  </tr>

  <tr>

   <td width="27">5</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

  <tr>

   <td width="27">6</td>

   <td width="22">S</td>

   <td width="22">G</td>

   <td width="22">g</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">G</td>

  </tr>

  <tr>

   <td width="27">7</td>

   <td width="22"></td>

   <td width="22">G</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">g</td>

  </tr>

  <tr>

   <td width="27">8</td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

 </tbody>

</table>




Black shoots at H1.  The rocket hits a grenade.  Black will lose a turn.  We now have:

<table width="201">

 <tbody>

  <tr>

   <td width="27"></td>

   <td width="22">A</td>

   <td width="22">B</td>

   <td width="22">C</td>

   <td width="22">D</td>

   <td width="22">E</td>

   <td width="22">F</td>

   <td width="22">G</td>

   <td width="22">H</td>

  </tr>

  <tr>

   <td width="27">1</td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">G</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">S</td>

   <td width="22">*</td>

  </tr>

  <tr>

   <td width="27">2</td>

   <td width="22"></td>

   <td width="22">g</td>

   <td width="22"></td>

   <td width="22">*</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

  </tr>

  <tr>

   <td width="27">3</td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

  <tr>

   <td width="27">4</td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">*</td>

   <td width="22">s</td>

  </tr>

  <tr>

   <td width="27">5</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

  <tr>

   <td width="27">6</td>

   <td width="22">S</td>

   <td width="22">G</td>

   <td width="22">g</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">G</td>

  </tr>

  <tr>

   <td width="27">7</td>

   <td width="22"></td>

   <td width="22">G</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">g</td>

  </tr>

  <tr>

   <td width="27">8</td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

 </tbody>

</table>




White shoots at H8.  Nothing.

<table width="201">

 <tbody>

  <tr>

   <td width="27"></td>

   <td width="22">A</td>

   <td width="22">B</td>

   <td width="22">C</td>

   <td width="22">D</td>

   <td width="22">E</td>

   <td width="22">F</td>

   <td width="22">G</td>

   <td width="22">H</td>

  </tr>

  <tr>

   <td width="27">1</td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">G</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">S</td>

   <td width="22">*</td>

  </tr>

  <tr>

   <td width="27">2</td>

   <td width="22"></td>

   <td width="22">g</td>

   <td width="22"></td>

   <td width="22">*</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

  </tr>

  <tr>

   <td width="27">3</td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

  <tr>

   <td width="27">4</td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">*</td>

   <td width="22">s</td>

  </tr>

  <tr>

   <td width="27">5</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

  <tr>

   <td width="27">6</td>

   <td width="22">S</td>

   <td width="22">G</td>

   <td width="22">g</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">G</td>

  </tr>

  <tr>

   <td width="27">7</td>

   <td width="22"></td>

   <td width="22">G</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">g</td>

  </tr>

  <tr>

   <td width="27">8</td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">*</td>

  </tr>

 </tbody>

</table>




White shoots again (remember, black lost a turn).  White shoots at G1.  It sinks another of white’s ships.

<table width="201">

 <tbody>

  <tr>

   <td width="27"></td>

   <td width="22">A</td>

   <td width="22">B</td>

   <td width="22">C</td>

   <td width="22">D</td>

   <td width="22">E</td>

   <td width="22">F</td>

   <td width="22">G</td>

   <td width="22">H</td>

  </tr>

  <tr>

   <td width="27">1</td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">G</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">*</td>

   <td width="22">*</td>

  </tr>

  <tr>

   <td width="27">2</td>

   <td width="22"></td>

   <td width="22">g</td>

   <td width="22"></td>

   <td width="22">*</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

  </tr>

  <tr>

   <td width="27">3</td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

  <tr>

   <td width="27">4</td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">*</td>

   <td width="22">s</td>

  </tr>

  <tr>

   <td width="27">5</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

  <tr>

   <td width="27">6</td>

   <td width="22">S</td>

   <td width="22">G</td>

   <td width="22">g</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">G</td>

  </tr>

  <tr>

   <td width="27">7</td>

   <td width="22"></td>

   <td width="22">G</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">g</td>

  </tr>

  <tr>

   <td width="27">8</td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">*</td>

  </tr>

 </tbody>

</table>




Black plays now.  He is a bit confused and shoots at H4.  He just sunk his own ship…

<table width="201">

 <tbody>

  <tr>

   <td width="27"></td>

   <td width="22">A</td>

   <td width="22">B</td>

   <td width="22">C</td>

   <td width="22">D</td>

   <td width="22">E</td>

   <td width="22">F</td>

   <td width="22">G</td>

   <td width="22">H</td>

  </tr>

  <tr>

   <td width="27">1</td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">G</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">*</td>

   <td width="22">*</td>

  </tr>

  <tr>

   <td width="27">2</td>

   <td width="22"></td>

   <td width="22">g</td>

   <td width="22"></td>

   <td width="22">*</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

  </tr>

  <tr>

   <td width="27">3</td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

  <tr>

   <td width="27">4</td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">*</td>

   <td width="22">*</td>

  </tr>

  <tr>

   <td width="27">5</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

  <tr>

   <td width="27">6</td>

   <td width="22">S</td>

   <td width="22">G</td>

   <td width="22">g</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">G</td>

  </tr>

  <tr>

   <td width="27">7</td>

   <td width="22"></td>

   <td width="22">G</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">g</td>

  </tr>

  <tr>

   <td width="27">8</td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">*</td>

  </tr>

 </tbody>

</table>




White shoots at a safe position H1.  It is a grenade that already exploded.  Nothing happens.

<table width="201">

 <tbody>

  <tr>

   <td width="27"></td>

   <td width="22">A</td>

   <td width="22">B</td>

   <td width="22">C</td>

   <td width="22">D</td>

   <td width="22">E</td>

   <td width="22">F</td>

   <td width="22">G</td>

   <td width="22">H</td>

  </tr>

  <tr>

   <td width="27">1</td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">G</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">*</td>

   <td width="22">*</td>

  </tr>

  <tr>

   <td width="27">2</td>

   <td width="22"></td>

   <td width="22">g</td>

   <td width="22"></td>

   <td width="22">*</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

  </tr>

  <tr>

   <td width="27">3</td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

  <tr>

   <td width="27">4</td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22">S</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">*</td>

   <td width="22">*</td>

  </tr>

  <tr>

   <td width="27">5</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

  </tr>

  <tr>

   <td width="27">6</td>

   <td width="22">S</td>

   <td width="22">G</td>

   <td width="22">g</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">G</td>

  </tr>

  <tr>

   <td width="27">7</td>

   <td width="22"></td>

   <td width="22">G</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">g</td>

  </tr>

  <tr>

   <td width="27">8</td>

   <td width="22"></td>

   <td width="22">s</td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22"></td>

   <td width="22">*</td>

  </tr>

 </tbody>

</table>

The game goes on until one player has all his/her ships sunk and he/she looses the game.




Your program must simulate a game of battleship between a human user (H) and a computer (C).  The program must:




<ul>

 <li>Ask H to place his/her ships and grenades.</li>

</ul>

For each ship and grenade, 1 coordinate will be entered (a character followed by an integer).  You can assume that the user will enter a character followed by an integer.  However, your program must check that the coordinates are within the grid and that there is nothing already at that position.  If the character is not between ‘A’ (or ‘a’) and ‘H’ (or ‘h’) or the integer is not between 1 and 8 or there is already a grenade or a ship at that position, then your program must display an error message and let the user try again.




<ul>

 <li>Place C’s own ships and grenades at random, making sure that the coordinates are valid and that there is nothing at that position already.</li>

</ul>




<ul>

 <li>Display the initial grid hiding all ships and grenades. To display the grid, use the following convention:

  <ul>

   <li>a position that has never been called should be displayed with the character ‘_’</li>

   <li>a position that has been called and hit a ship should be displayed with the character ‘s’ if the ship belongs to the user and ‘S’ if the ship belongs to the computer.</li>

   <li>a position that has been called and hit a grenade should be displayed with the character ‘g’ if the grenade belongs to the user and ‘G’ if the grenade belongs to the computer.</li>

   <li>a position that has been called and did not hit anything should be displayed with the character ‘*’</li>

   <li>a position that has already been called should be displayed the same way as it was after its first call</li>

  </ul></li>

</ul>




<ul>

 <li>Let H play first. Ask for the position of H’s rocket and modify the grid according to the rules of the game.  Then display the new grid showing only the positions that have been called to date using the convention above.</li>

</ul>

You can assume that the user will enter coordinates of the correct type (i.e. a character followed by an integer), but you must verify that the values are within the grid.  If the character is not between ‘A’ (or ‘a’) and ‘H’ (or ‘h’) or the integer is not between 1 and 8, then your program must display an error message and let the user try again.




<ul>

 <li>Let C play. Generate a random position for C’s rocket and modify the grid according to the rules of the game.  Then display the new gird showing only the positions that have been called to date using the convention above. To have C play, your program will simply generate a position at random every time.</li>

</ul>




<ul>

 <li>Keep simulating the game and display the grid after each turn, and eventually declare a winner.</li>

</ul>




<ul>

 <li>Once the winner is declared, the grid is then displayed showing the position of all ships and grenades. The program will display the number of missed turns due to hitting a grenade as described above.</li>

</ul>







Here is an example of how your program should behave (assume that the characters highlighted are entered by the user):




<table width="624">

 <tbody>

  <tr>

   <td width="624">Hi, let’s play Battleship!


    <table width="12">

     <tbody>

      <tr>

       <td width="12">A2 A0</td>

      </tr>

     </tbody>

    </table>Enter the coordinates of your ship #1: A1  Enter the coordinates of your ship #2: A1   sorry, coordinates already used.  try again.Enter the coordinates of your ship #2:Enter the coordinates of your ship #3:

    <table width="12">

     <tbody>

      <tr>

       <td width="12">D2A5A6D5</td>

      </tr>

     </tbody>

    </table>sorry, coordinates outside the grid.  try again.Enter the coordinates of your ship #3:Enter the coordinates of your ship #4:Enter the coordinates of your ship #5:   Enter the coordinates of your ship #6:


    <table width="12">

     <tbody>

      <tr>

       <td width="12">B3E3G3H3</td>

      </tr>

     </tbody>

    </table>Enter the coordinates of your grenade #1: H9 sorry, coordinates outside the grid.  try again. Enter the coordinates of your grenade #1: A1 sorry, coordinates already used.  try again. Enter the coordinates of your grenade #1:Enter the coordinates of your grenade #2:Enter the coordinates of your grenade #3:Enter the coordinates of your grenade #4: OK, the computer placed its ships and grenades at random.  Let’s play.position of your rocket: A3 ship hit._ _ S _ _ _ _ __ _ _ _ _ _ _ __ _ _ _ _ _ _ __ _ _ _ _ _ _ __ _ _ _ _ _  _ __ _ _ _ _ _ _ __ _ _ _ _ _ _ __ _ _ _ _ _ _ _position of my rocket: D8 nothing._ _ S _ _ _ _ __ _ _ _ _ _ _ __ _ _ _ _ _ _ __ _ _ _ _ _ _ __ _ _ _ _ _ _ __ _ _ _ _ _ _ __ _ _ _ _ _ _ __ _ _ * _ _ _ _position of your rocket: A4 ship hit._ _ S _ _ _ _ __ _ _ _ _ _ _ __ _ _ _ _ _ _ _S _ _ _ _ _ _ __ _ _ _ _ _ _ __ _ _ _ _ _ _ __ _ _ _ _ _ _ __ _ _ * _ _ _ _position of my rocket: H4 boom! grenade._ _ S _ _ _ _ __ _ _ _ _ _ _ __ _ _ _ _ _ _ _S _ _ _ _ _ _ g_ _ _ _ _ _ _ __ _ _ _ _ _ _ __ _ _ _ _ _ _ __ _ _ * _ _ _ _position of your rocket: H4 position already called._ _ S _ _ _ _ __ _ _ _ _ _ _ __ _ _ _ _ _ _ _S _ _ _ _ _ _ g_ _ _ _ _ _ _ __ _ _ _ _ _ _ __ _ _ _ _ _ _ __ _ _ * _ _ _ _    </td>

  </tr>

  <tr>

   <td width="624">  …&lt;after a difficult, but fair game…&gt;  … position of your rocket: E6 ship hit.  You Win! s _ S _ _ _ _ G s _ _  s _ _ G _ g _ _ g _ g g S _ S _ _ _ _ G s _ _ s _ _ _ _ s _ _ _ S _ _ _ S _ _ _ _ _ _ G_ _ _ _ _ _ S _ </td>

  </tr>

 </tbody>

</table>




<strong> </strong>

<h1>Object Oriented Design</h1>




The purpose of the assignment is to make you practice proper object-oriented design. Classes must de defined where appropriate, methods should be decomposed appropriately, information should be hidden (private, public, …) and enumerated types should be used where appropriate.  In particular, to represent the grid, you are expected to use a 2 dimensional array of objects, where each object represents a position in the grid and should be contain at least:

<ul>

 <li>the type of element at that position (a ship, a grenade or nothing)</li>

 <li>the owner of the element (the user or the computer)</li>

 <li>whether the position has already been called or not</li>

</ul>


