```
data = simulate(Y, final_time, nb_time_points=250) # invert Y(s)
```

simulate the output $y(t)$ of an LTI system, given the Laplace transform of the output, $Y(s)$, `Y`.

in other words, `simulate` inverts an expression in the frequency domain into the time domain.

# arguments

  * `Y::Union{TransferFunction, ClosedLoopTransferFunction}`: the Laplace transform of the output $y(t)$. usually formed by $g(s)U(s)$, where $U(s)$ is the Laplace transform of the input and $g(s)$ is the transfer function governing the dynamics of the system.
  * `final_time::Union{Int64, Float64}`: the duration over which to simulate the output of the LTI system, starting at time zero.
  * `nb_time_points::Int=100`: the number of time points at which to save the solution $y(t)$.

two time points preceding $t=0$ are included to illustrate that it is assumed $y(t)=0$ for $t<0$.

# returns

  * `data::DataFrame`: data frame containing two columns: `:t` for time $t$ and `:output` for $y(t)$. each row corresponds to a $(t_i, y(t_i))$ pair. i.e., row `i` of the `:t` column is time $i$, $t_i$, and row `i` of the `:output` column is $y_i=y(t_i)$. access the columns by `data[:, :t]` and `data[:, :output]`.

# examples

simulate the first order step response to a step, given the Laplace transform of the output, `Y`:

```jldoctest
g = 4 / (3 * s + 1)      # first-order transfer function g(s)
U = 1 / s                # unit step input U(s)
Y = g / s                # output Y(s)
data = simulate(Y, 12.0) # time series data frame
data[:, :t]              # array of time points tᵢ
data[:, :output]         # array of corresponding outputs y(tᵢ)
first(data, 5)           # show the first 5 rows of the data frame
# output
5×2 DataFrame
 Row │ t          output     
     │ Float64    Float64    
─────┼───────────────────────
   1 │ -0.6       0.0
   2 │ -1.0e-5    0.0
   3 │  1.0e-5    1.33333e-5
   4 │  0.123721  0.161606
   5 │  0.247432  0.316671
```
