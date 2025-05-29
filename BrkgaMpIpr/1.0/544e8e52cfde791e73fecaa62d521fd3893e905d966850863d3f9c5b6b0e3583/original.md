```
function path_relink!(brkga_data::BrkgaData,
    pr_type::PathRelinkingType,
    pr_selection::PathRelinkingSelection,
    compute_distance::Function,
    affect_solution::Function,
    number_pairs::Int64,
    minimum_distance::Float64,
    block_size::Int64,
    max_time::Float64,
    percentage::Float64
)::PathRelinkingResult
```

Perform path relinking between elite solutions that are, at least, a given minimum distance between themselves.

In the presence of multiple populations, the path relinking is performed between elite chromosomes from different populations, in a circular fashion. For example, suppose we have 3 populations. The framework performs 3 path relinkings: the first between individuals from populations 1 and 2, the second between populations 2 and 3, and the third between populations 3 and 1. In the case of just one population, both base and guiding individuals are sampled from the elite set of that population.

Note that the algorithm tries to find a pair of base and guiding solutions with a minimum distance given by the distance function. If this is not possible, a new pair of solutions are sampled (without replacement) and tested against the distance. In case it is not possible to find such pairs for the given populations, the algorithm skips to the next pair of populations (in a circular fashion, as described above). Yet, if such pairs are not found in any case, the algorithm declares failure. This indicates that the populations are very homogeneous.

If the found solution is the best solution found so far, IPR replaces the worst solution by it. Otherwise, IPR computes the distance between the found solution and all other solutions in the elite set, and replaces the worst solution by it if and only if the found solution is, at least, `minimum_distance` from all them.

The API will call `decode!()` function always with `writeback = false`. The reason is that if the decoder rewrites the chromosome, the path between solutions is lost and inadvertent results may come up. Note that at the end of the path relinking, the method calls the decoder with `writeback = true` in the best chromosome found to guarantee that this chromosome is re-written to reflect the best solution found.

This method is a multi-thread implementation. Instead of to build and decode each chromosome one at a time, the method builds a list of candidates, altering the alleles/keys according to the guide solution, and then decode all candidates in parallel. Note that `O(chromosome_size^2 / block_size)` additional memory is necessary to build the candidates, which can be costly if the `chromosome_size` is very large.

!!! warning
    As it is in [`evolve!()`](@ref), the decoding is done in parallel using threads, and the user **must guarantee that the decoder is THREAD-SAFE.** If such property cannot be held, we suggest using single thread by setting the environmental variable `JULIA_NUM_THREADS = 1` [(see Julia Parallel Computing)](https://docs.julialang.org/en/v1.1/manual/parallel-computing/).


# Arguments

  * [`brkga_data::BrkgaData`](@ref BrkgaData): the BRKGA data.
  * [`pr_type::PathRelinkingType`](@ref PathRelinkingType): type of path relinking to be performed. Either `DIRECT` or `PERMUTATION`-based.
  * [`pr_selection::PathRelinkingSelection`](@ref PathRelinkingSelection): selection of which individuals use to path relinking. Either `BESTSOLUTION` or `RANDOMELITE`.
  * `compute_distance::Function`: the function used to compute the distance between two chromosomes. The function **MUST HAVE** the following signature

    ```julia
    compute_distance(vector1::Array{Float64, 1},
                     vector2::Array{Float64, 1})::Float64
    ```
  * `affect_solution::Function`: function that takes two partial chromosomes / block of genes `block1` and `block2` and checks whether changing the keys from `block1` to `block2` affects the solution. For instance, suppose that the alleles/keys are used as threshold such that values > 0.5 activate a feature. Suppose we have `block1 = [0.3, 0.4, 0.1]` and `block2 = [0.4, 0.1, 0.2]`. Since all values are below 0.5, changing the keys from `block1` to `block2` do not change the solution, and therefore, we can drop such change (and subsequentely decoding). The blocks can hold only one key/allele, sequential key blocks, or even the whole chromosome. `affect_solution` takes two views/subarrays. The function **MUST HAVE** the following signature

    ```julia
    affect_solution(block1::SubArray{Float64, 1},
                    block2::SubArray{Float64, 1})::Bool
    ```

    !!! note
        This function depends on the problem structure and how the   keys/alleles are used
  * `number_pairs::Int64`: number of chromosome pairs to be tested.  If `number_pairs < 1`, all pairs are tested.
  * `minimum_distance::Float64`: minimum distance between two chromosomes computed by `compute_distance`.
  * `block_size::Int64 = 1`: number of alleles to be exchanged at once in each iteration. If one, the traditional path relinking is performed. It must be ≥ 1.
  * `max_time::Float64 = 0`: abort path-relinking when reach `max_time`. If `max_time ≤ 0`, no limit is imposed. Given in seconds.
  * `percentage::Float64 = 1.0`: define the size, in percentage, of the path to build. Range [0, 1].

# Returns

  * Returns [`PathRelinkingResult`](@ref) depending on the relink status.

# Throws

  * `ErrorException`: if [`initialize!()`](@ref) was not called before.
  * `ArgumentError`: when `percentage < 1e-6 || percentage > 1.0` and `block_size < 1`.
