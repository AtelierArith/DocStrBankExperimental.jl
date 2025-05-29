```
plot_setup(setup, [name]; [dsize=800, padding, displacements, stresses, reactions])
```

# Arguments

  * `setup::StaticSetup`: The setup to plot.
  * `name::String`: The filename or path (without extension) of the image to be created. If unspecified, image will be returned but not saved.
  * `dsize::Integer`: The diagonal pixel size of the image. The actual width and height will depend on the setup being plotted.
  * `padding::Float64`: The amount of extra distance to include on the border of the setup boundaries. 0 padding will make the image as small as possible, and you will likely lose details as they go off of the screen. Default is 0.4.

# Additional details that can be included.

  * `displacements`: Previously calculated displacements using `solve_displacements`.
  * `member_forces`: Previously calculated member forces using `solve_member_forces`.
  * `reactions`: Previously calculated reaction forces using `solve_reaction_forces`.
