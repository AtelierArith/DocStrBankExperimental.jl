```
anim_refine!([path], renderer,
             sol, planner, domain, state, spec;
             format="mp4", framerate=30, show=false,
             record_init=true, copy_sol=false, options...)

anim_refine!([anim|path], canvas, renderer,
             sol, planner, domain, state, spec;
             format="mp4", framerate=30, show=is_displayed(canvas),
             record_init=true, copy_sol=false, options...)
```

Uses `renderer` to animate the refinement of an existing solution by a SymbolicPlanners.jl `planner` in a PDDL `domain` (updating the `canvas` if one is provided).

Returns a tuple `(anim, sol)` where `anim` is an [`Animation`](@ref) object containing the animation, and `sol` is the solution returned by `planner`. If  `anim` is provided as the first argument, then additional frames are added to  the animation. Alternatively, if a `path` is provided, the animation is saved to that file, and `(path, sol)` is returned. If `copy_sol` is `true`, then a copy of the initial solution is made before refinement.

Note that once an animation is displayed or saved, no frames can be added to it.
