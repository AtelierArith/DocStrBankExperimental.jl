```
PMM_get_problem(fnum; uldim = 5, lldim = 5)
```

上位および下位の目的関数と、辞書形式の問題設定を返します。

### 例

```
julia> using HardTestProblems

julia> F, f, conf = PMM_get_problem(2,uldim=2,lldim=3);

julia> conf
Dict{Symbol, Any} with 15 entries:
  :follower_optimum      => 0.0
  :n_inequality_follower => 0
  :xbest                 => [0.0, 0.0]
  :problem               => "PMM2"
  :n_equality_follower   => 0
  :lldim                 => 3
  :uldim                 => 2
  :n_equality_leader     => 0
  :n_inequality_leader   => 0
  :xmin                  => [-10.0, -10.0]
  :leader_optimum        => 0.0
  :xmax                  => [10.0, 10.0]
  :ymax                  => [10.0, 10.0, 10.0]
  :ymin                  => [-10.0, -10.0, -10.0]
  :ybest                 => [0.0, 1.41421, 1.73205]

```
