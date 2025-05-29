```
simdat_crossed([RNG], subj_n, item_n;
               subj_btwn=nothing, item_btwn=nothing, both_win=nothing,
               subj_prefix="S", item_prefix="I")
```

Return a row table with a design specified by the:

  * number of subjects (`subj_n`),
  * number of items (`item_n`)
  * between-subject factors (`subj_btwn`)
  * between-item factors (`item_btwn`)
  * within-subject/item factors (`both_win`)

If a factor is both between-subject and between-item, put it in both `subj_btwn` and `item_btwn` with the same keys and the same levels.

Factors should be specified as dictionaries in the following format:

```julia
Dict(
    :factor1_name => ["F1_level1", "F1_level2"],
    :factor2_name => ["F2_level1", "F2_level2", "F2_level3"]
)
```

In addition to design, the rowtable contains a field `dv` pre-populated with N(0,1) noise as a basis for further simulating a design.

!!! note
    The number of subjects/items must divide the number of combinations of between subject/item factor levels. In other words, this function assumes a balanced design and will throw an error if that is not possible.

