```julia
printCSMHistorySequential(hists)
printCSMHistorySequential(hists, whichsteps)
printCSMHistorySequential(hists, whichsteps, fid)

```

Print a sequential summary lines of clique state machine histories in hists::Dict.

Notes

  * Slices are allowed, see examples.

Example

```julia
printCSMHistorySequential(hists)
printCSMHistorySequential(hists, 2=>46)
printCSMHistorySequential(hists, 1=>11:15)
printCSMHistorySequential(hists, [1,4,6]=>11:15)
printCSMHistorySequential(hists, [2=>45:52; 1=>10:15])
```

DevNotes

  * TODO perhaps move some of this functionality upstream to FSM
  * TODO upgrade to default `whichstep = :=>:` – i.e. 

      * add dispatch for `(:) |> typeof == Colon`,
      * `5:6=>:`.
  * TODO also add a elements between `Tuple{<:CSMRanges, Pair{<:CSMRanges,<:CSMRanges}}` option

      * ([1;3], 1=>5:7) which will print all steps from CSM 1 and 3, which occur between 1=>5 and 1=>7.
  * TODO maybe also `Dict(5=>5:8, 8=>20:25)`, or `Dict(2:5=>[1;3], 10=>1:5)`.

Related:

printHistoryLine, printCliqHistory
