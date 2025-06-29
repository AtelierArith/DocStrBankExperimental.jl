```
plotgrid!(GI, grid; annot=true, sides="WESN", fmt="", figname="", show=false)
```

Plot grid lines on top of an image created with the `worldrectangular` function.

  * `GI`: A GMTgrid or GMTimage data type.
  * `grid`: A vector of GMTdatset with meridians and parallels to be plotted. This is normaly produced  by the `graticules()` or `worldrectgrid()` functions.
  * `annot`: Wether to plot coordinate annotations or not (`annot=false`).
  * `sides`: Which sides of plot to annotate. `W` or `L` means annotate the left side and so on for any  combination of "WESNLRBT". To not annotate a particular side just omit that character. *e.g.*  `sides="WS"` will annotate only the left and bottom axes.
  * `figname`: To create a figure in local directory and with a name `figname`. If `figname` has an extension  that is used to select the fig format. *e.g.* `figname=fig.pdf` creates a PDF file localy called 'fig.pdf'
  * `fmt`: Create the raster figure in format `format`. Default is `fmt=:png`. To get it in PDF do `fmt=:pdf`
  * `show`: If `true`, finish and display the figure.
