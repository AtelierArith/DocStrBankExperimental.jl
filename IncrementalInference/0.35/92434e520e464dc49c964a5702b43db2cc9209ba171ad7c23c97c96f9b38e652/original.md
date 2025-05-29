```julia
animateCliqStateMachines(tree, cliqsyms, hists; frames)

```

Draw many images in '/tmp/?/csm_%d.png' representing time synchronized state machine events for cliques `cliqsyms::Vector{Symbol}`.

Notes

  * State history must have previously been recorded (stored in tree cliques).

Related

printCliqHistorySummary
