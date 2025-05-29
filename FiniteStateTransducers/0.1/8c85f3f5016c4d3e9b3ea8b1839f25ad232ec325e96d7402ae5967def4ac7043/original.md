`DFS(fst::WFST, initial; filter=arc->true)`

Creates an iterator that performs a depth-first search (DFS) of the `fst` starting from the state `initial`. The function filter can be specify in order to perform the search ignoring arcs with user-defined properties.

For each iterator the tuple `(p,s,n,d,e)` is returned, where: 

  * `p` is the parent parent state (p==0 if there is no parent)
  * `s` is the current state
  * `n` next state: `n==0` if `s` has no arcs or if completely explored. These will give you standard DFS iterations.
  * `d` is a `Bool`: if `true` means a new state is discovered, can be used to pick up DFS its (see example below)
  * `e` is a `Bool`, if `true` means all arcs have been inspected
  * `a` inspected arc (empty if `d == false`)

The following cases/colors are possible:

  * `d == false && n ==0` -> black state, state has been checked completely
  * `d == false && n !=0` -> `n` is already gray
  * `d == true -> n` state is colored gray, i.e. is visited for the first time

# Example

```julia
julia> fst = WFST(Dict(1=>1));

julia> add_arc!(fst, 1, 2, 1, 1, 1.0);

julia> add_arc!(fst, 1, 5, 1, 1, 1.0);

julia> add_arc!(fst, 1, 3, 1, 1, 1.0);

julia> add_arc!(fst, 2, 6, 1, 1, 1.0);

julia> add_arc!(fst, 2, 4, 1, 1, 1.0);

julia> add_arc!(fst, 5, 4, 1, 1, 1.0);

julia> add_arc!(fst, 3, 4, 1, 1, 1.0);

julia> add_arc!(fst, 3, 7, 1, 1, 1.0);

julia> initial!(fst,1)
WFST #states: 7, #arcs: 8, #isym: 1, #osym: 1
|1/0.0f0|
1:1/1.0f0 → (2)
1:1/1.0f0 → (5)
1:1/1.0f0 → (3)
(2)
1:1/1.0f0 → (6)
1:1/1.0f0 → (4)
(3)
1:1/1.0f0 → (4)
1:1/1.0f0 → (7)
(4)
(5)
1:1/1.0f0 → (4)
(6)
(7)

julia> dfs = FiniteStateTransducers.DFS(fst,1); # DFS starting from state 1

julia> for (p,s,n,d,e,a) in dfs
         println("$p,$s,$n")
         if d == true
           println("visiting first time $n (Gray)")
         else
           if e
             println("completed state $s (Black)")
           else
             println("node $n already visited")
           end
         end
       end
0,1,2
visiting first time 2 (Gray)
1,2,6
visiting first time 6 (Gray)
2,6,0
completed state 6 (Black)
1,2,4
visiting first time 4 (Gray)
2,4,0
completed state 4 (Black)
1,2,0
completed state 2 (Black)
0,1,5
visiting first time 5 (Gray)
1,5,4
node 4 already visited
1,5,0
completed state 5 (Black)
0,1,3
visiting first time 3 (Gray)
1,3,4
node 4 already visited
1,3,7
visiting first time 7 (Gray)
3,7,0
completed state 7 (Black)
1,3,0
completed state 3 (Black)
0,1,0
completed state 1 (Black)

```
