```
function SegmentIntegrator(
	EG::ElementGeometry,
	[kernel!::Function],
	oa_args::Array{<:Tuple{<:Any, DataType},1};
	kwargs...)
```

Generates an SegmentIntegrator that can integrate over segments of the specified geometry EG. To do so, it evaluates, at each quadrature point, the specified operator evaluations, postprocesses them with the kernel function (if provided) and accumulates the results with the quadrature weights. If no kernel is given, the arguments are integrated directly. If a kernel is provided it has be conform to the interface

```
kernel!(result, eval_args, qpinfo)
```

where qpinfo allows to access information at the current quadrature point. Additionally the length of the result needs to be specified via the kwargs.

Evaluation can be triggered via the integrate_segment! function after an initialize!

Operator evaluations are tuples that pair a tag (to identify an unknown or the position in the vector) with a FunctionOperator.

Keyword arguments:

  * factor: factor that should be multiplied during assembly. Default: 1
  * resultdim: dimension of result field (default = length of arguments). Default: 0
  * matrix_mode: integrator integrates basis functions of FEspace separately to assembly a matrix that maps solution to segment integrations (requires that kernel is linear). Default: false
  * name: name for operator used in printouts. Default: ''SegmentIntegrator''
  * params: array of parameters that should be made available in qpinfo argument of kernel function. Default: nothing
  * quadorder: quadrature order. Default: ''auto''
  * bonus_quadorder: additional quadrature order added to quadorder. Default: 0
  * entry*tolerance: threshold to add entry to sparse matrix (only in matrix*mode). Default: 0
  * verbosity: verbosity level. Default: 0
