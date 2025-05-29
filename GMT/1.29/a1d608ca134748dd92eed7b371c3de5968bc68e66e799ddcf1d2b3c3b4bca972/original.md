```
movie(main; pre=nothing, post=nothing, kwargs...)
```

Create animation sequences and movies.

See full GMT (not the `GMT.jl` one) docs at [`movie`](http://docs.generic-mapping-tools.org/latest/movie.html)

## Parameters

  * **main** :: [Type => Str]

    Name of a stand-alone GMT.jl script that makes the frame-dependent plot.``
  * **C** | **canvas** :: [Type => Str]

    Specify the canvas size used when composing the movie frames.   (http://docs.generic-mapping-tools.org/latest/movie.html#c)
  * **N** | **name** :: [Type => Str]

    Determines the name of a sub-directory with frame images as well as the final movie file.   (http://docs.generic-mapping-tools.org/latest/movie.html#n)
  * **T** | **frames** :: [Type => Int | Str]

    Either specify how many image frames to make or supply a file with a set of parameters, one record per frame (i.e., row).    (http://docs.generic-mapping-tools.org/latest/movie.html#t)
  * **pre** :: [Type => Str]

    The optional *backgroundscript* file (a GMT.jl script) can be used one or two purposes: (1) It may create files   (such as timefile) that will be needed by mainscript to make the movie, and (2) It may make a static background   plot that should form the background for all frames.   (http://docs.generic-mapping-tools.org/latest/movie.html#s)
  * **post** :: [Type => Str]

    The optional *foregroundscript* file (a GMT.jl script) can be used to make a static foreground plot that should be overlain on all frames.    (http://docs.generic-mapping-tools.org/latest/movie.html#s)
  * **A** | **gif** :: [Type => Str]		$Args = [+l[n]][+sstride]$

    Build an animated GIF file. You may specify if the movie should play more than once and if so append how many times to repeat.   (http://docs.generic-mapping-tools.org/latest/movie.html#a)
  * **D** | **frame_rate** :: [Type => Int]

    Set the display frame rate in frames per seconds for the final animation [24].   (http://docs.generic-mapping-tools.org/latest/movie.html#d)
  * **E** | **titlepage** :: [Type => Str | tuple]

    Give a titlepage script that creates a static title page for the movie [no title].    (http://docs.generic-mapping-tools.org/latest/movie.html#e)
  * **F** | **format** :: [Type => Str]	$Arg = format[+ooptions]$

    Set the format of the final video product. Choose either mp4 (MPEG-4 movie) or webm (WebM movie).   (http://docs.generic-mapping-tools.org/latest/movie.html#f)
  * **G** | **fill** :: [Type => Str | Int | Touple]

    Set the canvas color or fill before plotting commences [none].   (http://docs.generic-mapping-tools.org/latest/movie.html#g)
  * **H** | **scale** :: [Type => Number]

    Temporarily increases the effective dots-per-unit by factor, rasterizes the frame, then downsamples the image by the same factor at the end.   (http://docs.generic-mapping-tools.org/latest/movie.html#h)
  * **I** | **includefile** :: [Type => Str]

    Insert the contents of includefile into the movie_init script that is accessed by all movie scripts.   (http://docs.generic-mapping-tools.org/latest/movie.html#i)
  * **K** | **fading** :: [Type => Number | Str | Tuple]	$Arg = [+f[i|o]fade[s]][+gfill][+p] ]$

    Add fading in and out for the main animation sequence [no fading].   (http://docs.generic-mapping-tools.org/latest/movie.html#k)
  * **L** | **label** :: [Type => Str]

    Automatic labeling of individual frames.   (http://docs.generic-mapping-tools.org/latest/movie.html#l)
  * **M** | **cover_page** :: [Type => number]	$Arg = frame[,format]$

    Select a single frame for a cover page. This frame will be written to the current directory.   (http://docs.generic-mapping-tools.org/latest/movie.html#m)
  * **P** | **progress** :: [Type => Str | Tuple]

    Automatic placement of progress indicator(s).   (http://docs.generic-mapping-tools.org/latest/movie.html#p)
  * **Q** | **debug** :: [Type => Bool | Str]		$Arg = [s]$

    Debugging: Leave all files and directories we create behind for inspection.   (http://docs.generic-mapping-tools.org/latest/movie.html#q)
  * **Sb** | **background** :: [Type => Str | Function]

    Optional background script or bg PS file [GMT6.1 only](http://docs.generic-mapping-tools.org/latest/movie.html#s)
  * **Sf** | **foreground** :: [Type => Str | Function]

    Optional foreground script or fg PS file [GMT6.1 only](http://docs.generic-mapping-tools.org/latest/movie.html#s)
  * **W** | **work_dir** :: [Type => Str]

    By default, all temporary files and frame PNG file are built in the subdirectory prefix set via **name**.   You can override that by giving another workdir as a relative or full directory path.   (http://docs.generic-mapping-tools.org/latest/movie.html#w)
  * **Z** | **clean** :: [Type => Bool]

    Erase the entire **name** directory after assembling the final movie [Default leaves directory with all images.   (http://docs.generic-mapping-tools.org/latest/movie.html#z)
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    Select verbosity level, which will send progress reports to stderr.
  * **x** | **cores** | **n_threads** :: [Type => Str or Number]  $Arg = [[-]n]$

    Limit the number of cores to be used in any OpenMP-enabled multi-threaded algorithms.   (http://docs.generic-mapping-tools.org/latest/gmt.html#x-full)
