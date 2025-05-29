```
function Pointevaluator(
	[kernel!::Function],
	oa_args::Array{<:Tuple{<:Any, DataType},1};
	kwargs...)
```

Generates a PointEvaluator that can evaluate the specified operator evaluations at arbitrary points. If no kernel function is given, the arguments are given directly. If a kernel is provided, the arguments are postprocessed accordingly and the kernel has to be conform to the interface

```
kernel!(result, eval_args, qpinfo)
```

where qpinfo allows to access information at the current evaluation point. Additionally the length of the result needs to be specified via the kwargs.

Evaluation can be triggered via the evaluate function after an initialize! call.

Operator evaluations are tuples that pair a tag (to identify an unknown or the position in the vector) with a FunctionOperator.

Keyword arguments:

  * resultdim: dimension of result field (default = length of operators). Default: 0
  * params: array of parameters that should be made available in qpinfo argument of kernel function. Default: nothing
  * name: name for operator used in printouts. Default: ''PointEvaluator''
  * verbosity: verbosity level. Default: 0
