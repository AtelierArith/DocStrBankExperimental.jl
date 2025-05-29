# Function call

`save3fig(fileName, subDir="."; dpi=300, tight=true, crop=false)`

# Description

Save the actual figure in the following three file formats

  * `png` Portable network graphics in subdirectory png/
  * `eps` Encapsulated postscript in subdirectory eps/
  * `pdf` Encapsulated postscript in subdirectory pdf/

These three graphics format are relevant when processing figures in LaTeX, LyX, LibreOffice or other word processors

# Variables

`fileName` String of the filename, extended by `.png`, `.eps` and `.pdf`; the file names are stored in sub directories `png/`, `eps/` and `pdf/`

`subDir` String of sub directory in which the adjacent sub directories  `png/`, `eps/` and `pdf/` are located; default = `.` (local work directory)

`dpi` Resolution of the stored PNG file; default = 300 (dpi)

`tight` Additional margin around the figure is removed, except for a 2% margin; default = `true`

`crop` Crop all 'white' space around the figure; this feature requires the installation of the following software

  * imagemagick to be applied to `png` files, see https://www.imagemagick.org/script/index.php on Windows or apply `sudo apt install imagemagick` on Linux (Mint or Ubuntu)
  * epstool to be applied to `eps` files, see http://pages.cs.wisc.edu/~ghost/gsview/epstool.htm on Windows or apply `sudo apt install epstool` on Linux (Mint or Ubuntu)
  * pdfcrop to be applied to `pdf` files, see https://www.ctan.org/pkg/pdfcrop on Windows or apply `sudo apt install texlive-extra-utils` on Linux (Mint or Ubuntu)

# Examples

```julia
julia> save3fig("phasordiagram")
julia> save3fig("phasordiagram_crop", crop=true)
```
