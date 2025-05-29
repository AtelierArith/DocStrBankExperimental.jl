```
Plot the objective function error obtained from SpaceSolutionRef2D and
SpaceSolutionTra2D for the space solution given.

    plot(SpaceSolution(),
            x1, x2, S;
            lims=[x1[1], x1[end], x2[1], x2[end]], num_levels=80, s=(640,480)
    )
    gui()

        x1: range of first dimension
        x2: range of second dimension
        S: matrix with the objective function values
        Optional:
            lims: limits of the two axes
            num_levels: number of levels of the contour plot
            s: size of the figure
```
