```
mjd_subQuat(qa, qb, Da, Db)
```

Derivatives of mju_subQuat.

# Arguments

  * **`qa::Vector{Float64}`** -> A vector of variable size. `qa` should be a vector, not a matrix. `qa` must have size 4. Constant.
  * **`qb::Vector{Float64}`** -> A vector of variable size. `qb` should be a vector, not a matrix. `qb` must have size 4. Constant.
  * **`Da::Matrix{Float64}`** -> An **optional** matrix of variable size. `Da` must have size 9. Can set to `nothing` if not required.
  * **`Db::Matrix{Float64}`** -> An **optional** matrix of variable size. `Db` must have size 9. Can set to `nothing` if not required.
