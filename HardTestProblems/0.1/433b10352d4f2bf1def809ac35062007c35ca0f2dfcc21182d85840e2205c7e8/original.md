```
SMD_get_problem(fnum; uldim = 2, lldim = 3)
```

Return upper and lower level objective functions, and the problem configuration in a dictionary.

### Example

```juliarepl
julia> using HardTestProblems

julia> F, f, conf = SMD_get_problem(12,uldim=2,lldim=3);

julia> conf
Dict{Symbol, Any} with 14 entries:
  :follower_optimum      => 4.0
  :n_inequality_follower => 3
  :xbest                 => [1.0, 1.0]
  :n_equality_follower   => 0
  :lldim                 => 3
  :uldim                 => 2
  :n_equality_leader     => 0
  :n_inequality_leader   => 3
  :xmin                  => [-5.0, -1.0]
  :leader_optimum        => 3.0
  :xmax                  => [10.0, 1.0]
  :ymax                  => [10.0, 10.0, 0.785388]
  :ymin                  => [-5.0, -5.0, -0.785388]
  :ybest                 => [1.0, 1.0, 0.0]

julia> F(conf[:xbest], conf[:ybest]) # upper level function
(3.0, [-0.0, -0.0, -1.0], [0.0])

julia> f(conf[:xbest], conf[:ybest]) # lower level function
(4.0, [-0.0, -0.0, -0.0], [0.0])

```
