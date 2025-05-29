```
showfig([fmt="format", figname="figname[.fmt]"])
```

Finish the PostScript file and convert&display the figure.

  * `fmt`: Create the raster figure in format `format`. Default is `fmt=:png`. To get it in PDF do `fmt=:pdf`
  * `figname`: To create a figure in local directory and with a name `figname`. If `figname` has an extension,  that is used to select the fig format. *e.g.* `figname=fig.pdf` creates a PDF file localy called 'fig.pdf'
