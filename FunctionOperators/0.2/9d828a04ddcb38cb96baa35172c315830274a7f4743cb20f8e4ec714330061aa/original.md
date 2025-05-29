Object that holds global settings for `FunctionOperators` library

Fields:

  * `verbose::Bool` If set to true, then allocation information and calculated plan function will be displayed upon creation (i.e., when a composite operator is first used). Default: `false`
  * `macro_verbose::Bool` If set to true, then recycling macros (@♻ and @recycle) will print the transformed code. Default: `false`
  * `auto_reshape::Bool` If set to true, then input and output is reshaped according to the inDims and outDims values of the FunctionOperator before and after any multiplication. Default: `false`
