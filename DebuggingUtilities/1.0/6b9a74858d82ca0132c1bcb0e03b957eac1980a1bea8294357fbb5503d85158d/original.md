DebuggingUtilities contains a few tools that may help debug julia code. The exported tools are:

  * `@showln`: like `@show`, but displays file and line number information as well
  * `@showlnt`: like `@showlnt`, but also uses indentation to display recursion depth
  * `test_showline`: a function that displays progress as it executes a file
  * `time_showline`: a function that displays execution time for each expression in a file
