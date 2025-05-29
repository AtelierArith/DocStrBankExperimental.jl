```
stateSelectionFunctions = StateSelection.StateSelectionFunctions(;
    var_name               = v          -> nothing,
    var_julia_name         = v          -> nothing,
    var_unit               = v          -> "",
    var_startInitFixed     = v          -> (nothing,false),   # (startOrInit, fixed)
    var_is_state           = v_original -> false,
    equation               = e          -> ""
    isSolvableEquation     = (e_original,v_original) -> false,
    isLinearEquation       = (e_original,v_original) -> (false, false),
    getSolvedEquationAST   = (e, v)                  -> nothing,
    getResidualEquationAST = (e, residualName)       -> nothing,
    showMessage            = (message; severity=0,from="???",details="",variables=Int[],equations=Int[]) -> println("...")
)
```

Generate an instance of an immutable struct that holds the callback functions as needed by [`getSortedAndSolvedAST`](@ref).

The functions need to have the following arguments:

  * `var_name(v::Int)::String`:
     Return full (Modia) path name of `v` as String (e.g. `"a.b.c"` or `"a.b.der(c)"`).
  * `var_julia_name(v::Int)::String`:
    Return full Julia path name of variable `v` as `Symbol` (e.g. Symbol("m.a.b.c") or Symbol("a*b*der_c")).
  * `var_unit(v::Int)::String`:
    Return unit of variable `v` as `String` (for example "N*m") or `""`, if no unit is defined.
  * `var_startInitFixed(v::Int)::Tuple(Any,Bool)`:
    Return `(startOrInit, fixed)`, where `startOrInit` is the `start` or `init` value or `nothing` (if neither `start` nor `init` defined) and `fixed` is `true`, if an `init` value is defined.
  * `var_is_state(v_original::Int)::Bool`:
     Return true, if variable `v_original` is defined to be a state.
  * `equation(e::Int)`:
     Return equation as string or "", if equation is not provided.
  * `isSolvableEquation(e_original::Int, v_original::Int)::Bool`:
     Return `true` if original, undifferentiated equation `e_original`  can be uniquely solved for variable `v_original`.
  * `(isLinear, hasConstantCoefficient) = isLinearEquation(e_original::Int, v_original::Int)`:
     Return the information whether the original, undifferentiated equation `e`  is **linear** with respect to variable `v` (`isLinear=true`) and if this is the case whether  the coefficient of this linear term is **constant** after initialization  (`hasConstantCoefficient=true`). If `v` is an array, then the array equation `e` must  be linear with respect to all elements of array `v` in order to return `isLinear=true`.
  * `AST = getSolvedEquationAST(e:Int, v:Int)`:
    Return Abstract Syntax Tree `AST::Expr` of equation `e` solved for variable `v` as instance of `Expr`.
  * `AST = getResidualEquationAST(e::Int, residualName::Symbol)`:
    Return Abstract Syntax Tree `AST::Expr` of eqation `e` as residual equation with ustrip(..) 
    `residualName = ustrip( < residual form of equation e> )`
  * `showMessage(message; severity=0,from="???",details="",variables=Int[],equations=Int[])`:
    Print information, warning or error message.
