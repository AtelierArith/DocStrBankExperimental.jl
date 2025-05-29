CodeTracking can be thought of as an extension of InteractiveUtils, and pairs well with Revise.jl.

  * `code_string`, `@code_string`: fetch the source code (as a string) for a method definition
  * `code_expr`, `@code_expr`: fetch the expression for a method definition
  * `definition`: a lower-level variant of the above
  * `pkgfiles`: return information about the source files that define a package
  * `whereis`: Return location information about methods (with Revise, it updates as you edit files)
  * `signatures_at`: return the signatures of all methods whose definition spans the specified location
