```
branchandbound_frob_matrixcomp(
    k::Int,
    A::Array{Float64, 2},
    indices::BitMatrix,
    γ::Float64,
    λ::Float64,
    noise::Bool,
    ;
    <keyword arguments>
)
```

Complete matrix `A` with observed indices in `indices` with rank-`k` matrix `X`.

In the noisy case (`noise == true`), solves (with regularization parameter `γ`):

$$
\min_{\mathbf{X}}
\frac{1}{2} \sum_{(i,j) \in \mathcal{I}} (X_{i,j} - A_{i,j})^2 
+ \frac{1}{2 \gamma} \|\mathbf{X}\|_F^2
\quad 
\text{s.t. } \text{Rank}(\mathbf{X}) \leq k
$$

In the noiseless case (`noise == false`), solves:

$$
\min_{\mathbf{X}}
\|\mathbf{X}\|_F^2
\quad 
\text{s.t. } X_{i,j} = A_{i,j} \ \forall (i,j) \in \mathcal{I}, 
\ \text{Rank}(\mathbf{X}) \leq k
$$

# Arguments

  * `branching_type::Union{String, Nothing} = nothing`: in the situation with `use_disjunctive_cuts = false`, determining which coordinate to branch on: either "lexicographic" or "bounds" or "gradient";
  * `branch_point::Union{String, Nothing} = nothing`: in the situation with `use_disjunctive_cuts = false`, determine which value to branch on: either "midpoint" or "current_point"
  * `node_selection::String = "breadthfirst"`: the node selection strategy to use: either "breadthfirst" or "bestfirst" or "depthfirst" or "bestfirst_depthfirst";
  * `bestfirst_depthfirst_cutoff::Int = 10000`: in the situation with `node_selection = "bestfirst_depthfirst"`, the number of nodes in the queue before the algorithm switches from `"bestfirst"` to `"depthfirst"`;
  * `gap::Float64 = 1e-4`: relative optimality gap for branch-and-bound algorithm;
  * `use_disjunctive_cuts::Bool = true`: whether to use eigenvector disjunctions, highly recommended to be `true`;
  * `disjunctive_cuts_type::Union{String, Nothing} = nothing`: number of pieces in piecewise linear upper-approximation; either "linear" (2 pieces) or "linear2" (3 pieces) or "linear3" (4 pieces);
  * `disjunctive_cuts_breakpoints::Union{String, Nothing} = nothing`: number of eigenvectors to use in constructing separation oracle, either "smallest*1*eigvec" (most negative eigenvector) or "smallest*2*eigvec" (combination of first and second most negative eigenvectors);
  * `presolve::Bool = false`: in the noiseless setting (`noise = false`), whether to perform presolve, highly recommended to be `true`;
  * `add_basis_pursuit_valid_inequalities::Bool = false`: in the noiseless setting (`noise = false`), whether to impose valid inequalities from determinant minors;
  * `add_Shor_valid_inequalities::Bool = false`: whether to add Shor SDP inequalities to strengthen SDP relaxation at each node;
  * `Shor_valid_inequalities_noisy_rank1_num_entries_present::Vector{Int} = [1, 2, 3, 4]`: if `add_Shor_valid_inequalities` is true, the set of 2-by-2 determinant minors to model with Shor SDP inequalities, based on the number of filled entries (should be some subset of `[1, 2, 3, 4]`);
  * `add_Shor_valid_inequalities_fraction::Float64 = 1.0`: if `add_Shor_valid_inequalities` is true, the proportion of 2-by-2 determinant minors to model with Shor SDP inequalities;
  * `add_Shor_valid_inequalities_iterative::Bool = false`: if `add_Shor_valid_inequalities` is true, whether to add them iteratively from parent node to child node;
  * `max_update_Shor_indices_probability::Float64 = 1.0`: if `add_Shor_valid_inequalities_iterative` is true, the maximum probability of adding inequalities at a node;
  * `min_update_Shor_indices_probability::Float64 = 0.1`, if `add_Shor_valid_inequalities_iterative` is true, the minimum probability of adding inequalities at a node;
  * `update_Shor_indices_probability_decay_rate::Float64 = 1.1`: if `add_Shor_valid_inequalities_iterative` is true, the base of the exponential decay of the probability of adding inequalities at a node, as a function of depth in the tree;
  * `update_Shor_indices_n_minors::Int = 100`: if `add_Shor_valid_inequalities_iterative` is true, the number of Shor SDP inequalities to add at a node whenever adding is performed;
  * `root_only::Bool = false`: if true, only solves relaxation at root node
  * `altmin_flag::Bool = true`: whether to perform alternating minimization at nodes in the branch-and-bound tree, highly recommended to be `true`;
  * `max_altmin_probability::Float64 = 1.0`: if `altmin_flag` is true, the maximum probability of performing alternating minimization at a node;
  * `min_altmin_probability::Float64 = 0.005`: if `altmin_flag` is true, the minimum probability of performing alternating minimization at a node;
  * `altmin_probability_decay_rate::Float64 = 1.1`: if `altmin_flag` is true, the base of the exponential decay of the probability of performing alternating minimization at a node, as a function of depth in the tree;
  * `use_max_steps::Bool = false`: whether to terminate the algorithm based on the number of branch-and-bound nodes explored;
  * `max_steps::Int = 1000000`: if `use_max_steps` is true, the upper limit on number of branch-and-bound nodes explored;
  * `time_limit::Int = 3600`: time limit in seconds
  * `update_step::Int = 1000`: number of branch-and-bound nodes explored per printed update
