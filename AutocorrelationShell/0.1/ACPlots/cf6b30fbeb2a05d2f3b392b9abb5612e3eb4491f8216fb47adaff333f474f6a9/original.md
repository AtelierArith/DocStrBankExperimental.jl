```
wiggle(wav; taxis=1:size(wav,1), zaxis=1:size(wav,2), sc=1, EdgeColor=:black, FaceColor=:black, Orient=:across, Overlap=true, ZDir=:normal)
```

Plot a set of shaded wiggles

# Arguments

  * `wav::Array`: matrix of waveform columns.
  * `taxis::Array=1:size(wav,1)`: time axis vector
  * `zaxis::Array=1:size(wav,2)`: space axis vector
  * `sc::Float=1`: scale factor/magnification.
  * `EdgeColor::Symbol=:black`: Sets edge of wiggles color.
  * `FaceColor::Symbol=:black`: Sets shading color of wiggles.
  * `Overlap::bool=true`: How signals are scaled.       true  - Signals overlap (default);       false - Signals are scaled so they do not overlap.
  * `Orient::Symbol=:across`: Controls orientation of wiggles.       :across - from left to right       :down   - from top to down
  * `ZDir::Symbol=:normal`: Direction of space axis.       :normal  - First signal at bottom (default)       :reverse - First signal at top.

Translated by Nicholas Hausch – MATLAB file provided by Naoki Saito The previous MATLAB version contributors are:  Anthony K. Booer (SLB) and Bradley Marchand (NSWC-PC) Revised by Naoki Saito, Feb. 05, 2018
