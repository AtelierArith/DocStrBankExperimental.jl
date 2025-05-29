```
PolicyGraphGenerator
```

  * `fast = false` use fast (but very picky) alternate parser for .pomdp files
  * `graph_max_depth` maximum horizon of the generated policy graph. There is no limit by default.
  * `graph_max_branch` maximum number of branches of the generated policy graph. Shown will be top in probability. There is no limit by default.
  * `graph_min_prob` minimum probability threshold for a branch to be shown in the policy graph defaults to zero
  * `graph_filename` output name for the DOT file to be generated
  * `pomdp_filename` pomdp file input
  * `policy_filename` policy file input
