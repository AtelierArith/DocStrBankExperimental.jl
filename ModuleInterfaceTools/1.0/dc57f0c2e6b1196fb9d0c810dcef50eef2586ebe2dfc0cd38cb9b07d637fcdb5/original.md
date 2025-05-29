@api <cmd> [<symbols>...]

  * freeze                # use at end of module to freeze API
  * list     <modules>... # list API(s) of given modules (or current if none given)
  * use      <modules>... # use, without importing (i.e. can't extend)
  * use!     <modules>... # use, without importing (i.e. can't extend), "export"
  * test     <modules>... # using public and develop APIs, for testing purposes
  * extend   <modules>... # for development, imports api & dev, use api & dev definitions
  * extend!  <modules>... # for development, imports api & dev, use api & dev definitions, "export"
  * reexport <modules>... # export public definitions from those modules
  * base     <names...>   # Add functions from Base that are part of the API (extendible)
  * base!    <names...>   # Add functions from Base or define them if not in Base
  * public   <names...>   # Add other symbols that are part of the public API (structs, consts)
  * public!  <names...>   # Add functions that are part of the public API (extendible)
  * develop  <names...>   # Add other symbols that are part of the development API
  * develop! <names...>   # Add functions that are part of the development API (extendible)
  * define!  <names...>   # Define functions to be extended, public API
  * defdev!  <names...>   # Define functions to be extended, develop API
  * modules  <names...>   # Add submodule names that are part of the API
  * path     <paths...>  # Add paths to LOAD_PATH
  * def <name> <expr>    # Same as the @def macro, creates a macro with the given name
