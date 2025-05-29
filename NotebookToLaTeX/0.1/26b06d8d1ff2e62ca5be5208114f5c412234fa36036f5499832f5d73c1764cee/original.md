```
notebooktolatex(notebook, targetdir="./build_latex"; template=:book, fontpath=nothing)
```

Takes a notebook file, converts it to LaTeX and creates a file structure with figures, fonts and listing files.

  * `targetdir` is the target directory where the LaTeX project will be created.

If the directory does not exist, it is created.

  * `template` - The template for the LaTeX file. It's based on LaTeX templates.

Current supported templates are `:book`, `:mathbook`.

  * `fontpath` - The output LaTeX files uses JuliaMono fonts in order to support the

unicodes that are also supported in Julia. If the user already has JuliaMono installed, he can provide the path to where the `.ttf` files are stored. If `nothing` is passed, then the font files will be downloaded and saved in the `./fonts/` folder.
