```julia
bifurcationdiagram!(
    prob,
    node,
    maxlevel,
    options;
    code,
    halfbranch,
    verbosediagram,
    kwargs...
)

```

Similar to [`bifurcationdiagram`](@ref) but you pass a previously computed `node` from which you want to further compute the bifurcated branches. It is usually used with `node = get_branch(diagram, code)` from a previously computed bifurcation `diagram`.

# Arguments

  * `node::BifDiagNode` a node in the bifurcation diagram
  * `maxlevel = 1` required maximal level of recursion.
  * `options = (x, p, level; k...) -> contparams` this function allows to change the [`continuation`](@ref) options depending on the branching `level`. The argument `x, p` denotes the current solution to `F(x, p)=0`.

# Optional arguments

  * `code = "0"` code used to display iterations
  * `usedeflation = false`
  * `halfbranch = false` for Pitchfork / Transcritical bifurcations, compute only half of the branch. Can be useful when there are symmetries.
  * `verbosediagram` verbose specific to bifurcation diagram. Print information about the branches as they are being computed.
  * `kwargs` optional arguments as for [`continuation`](@ref) but also for the different versions listed in [Continuation](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/library/#Continuation-1).
