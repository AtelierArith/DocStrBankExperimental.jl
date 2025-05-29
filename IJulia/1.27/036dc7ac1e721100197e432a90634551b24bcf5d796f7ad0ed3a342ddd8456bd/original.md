**IJulia** is a [Julia-language](http://julialang.org/) backend combined with the [Jupyter](http://jupyter.org/) interactive environment (also used by [IPython](http://ipython.org/)).  This combination allows you to interact with the Julia language using Jupyter/IPython's powerful [graphical notebook](http://ipython.org/notebook.html), which combines code, formatted text, math, and multimedia in a single document.

The `IJulia` module is used in three ways

  * Typing `using IJulia; notebook()` will launch the Jupyter notebook interface in your web browser.  This is an alternative to launching `jupyter notebook` directly from your operating-system command line.
  * In a running notebook, the `IJulia` module is loaded and `IJulia.somefunctions` can be used to interact with the running IJulia kernel:

      * `IJulia.load(filename)` and `IJulia.load_string(s)` load the contents of a file or a string, respectively, into a notebook cell.
      * `IJulia.clear_output()` to clear the output from the notebook cell, useful for simple animations.
      * `IJulia.clear_history()` to clear the history variables `In` and `Out`.
      * `push_X_hook(f)` and `pop_X_hook(f)`, where `X` is either `preexecute`, `postexecute`, or `posterror`.  This allows you to insert a "hook" function into a list of functions to execute when notebook cells are evaluated.
      * `IJulia.set_verbose()` enables verbose output about what IJulia is doing internally; this is mainly used for debugging.
  * It is used internally by the IJulia kernel when talking to the Jupyter server.
