Due to code loading issues, this module will not function correctly if it is loaded using `atreplinit`. It must be loaded be loaded using a command line argument when julia is started:

e.g:   julia -i -e "using VimBindings; VimBindings.init()"
