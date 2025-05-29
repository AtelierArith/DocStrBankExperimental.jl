# Function call

`mmfwinding(w, i)`

# Description

Calculates the magnetomotive force distribution based on the winding layout and the actual currents of polyphase winding

# Input variable

`w[:,:]` Winding array with equal number of windings per slot, where

  * `size(w,1)` = number of layers, e.g. 1 or 2
  * `size(w,2)` = number of slots

`i[:]` Actual phase currents for, e.g.,  the three phases, scaled to 1

# Output variables

`mmf[:,:]` Magnetomotive force, where

  * `size(mmf,1)` = number phases
  * `size(mmm,1)` = number of slots
