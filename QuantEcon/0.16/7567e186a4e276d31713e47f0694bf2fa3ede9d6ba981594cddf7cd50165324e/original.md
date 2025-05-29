```
backward_induction(ddp, J[, v_term=zeros(num_states(ddp))])
```

Solve by backward induction a $J$-period finite horizon discrete dynamic  program with stationary reward $r$ and transition probability functions $q$ and discount factor $\beta \in [0, 1]$.

The optimal value functions $v^{\ast}_1, \ldots, v^{\ast}_{J+1}$ and  policy functions $\sigma^{\ast}_1, \ldots, \sigma^{\ast}_J$ are obtained by $v^{\ast}_{J+1} = v_{J+1}$, and

$$
v^{\ast}_j(s) = \max_{a \in A(s)} r(s, a) +
\beta \sum_{s' \in S} q(s'|s, a) v^{\ast}_{j+1}(s')
\quad (s \in S)
$$

and

$$
\sigma^{\ast}_j(s) \in \operatorname*{arg\,max}_{a \in A(s)}
            r(s, a) + \beta \sum_{s' \in S} q(s'|s, a) v^*_{j+1}(s')
            \quad (s \in S)
$$

for $j= J, \ldots, 1$, where the terminal value function $v_{J+1}$ is  exogenously given by `v_term`.

# Parameters

  * `ddp::DiscreteDP{T}` : Object that contains the Model Parameters
  * `J::Integer`: Number of decision periods
  * `v_term::AbstractVector{<:Real}=zeros(num_states(ddp))`: Terminal value  function of length equal to n (the number of states)

# Returns

  * `vs::Matrix{S}`: Array of shape (n, J+1) where `vs[:,j]`  contains the  optimal value function at period j = 1, ..., J+1.
  * `sigmas::Matrix{Int}`: Array of shape (n, J) where `sigmas[:,j]` contains the optimal policy function at period j = 1, ..., J.
