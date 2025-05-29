# `stochastic_heat_kernel_series!`

Compute the stochastic heat kernel, the result of $x = \exp(-t(I - P)) s $ where $s$ is a stochastic seed vector and $t$ is a time parameter and $P$ is a column-stochastic or sub-stochastic matrix. 

This function will return a vector $x$ such that $ \| x - x*{\mbox{exact}} \|*1 \le $ `eps`, and this function further guarantees  $x_{\mbox{exact}} - x \ge 0$.

The algorithm is just a direct evaluation of the power series represented by the heat kernel operation.  

** Expert interface, see `seeded_stochastic_heat_kernel`  for more user-friendly interfaces.**

## Inputs

-`x`: The solution vector  -`y`: An intermediate vector  -`z`: Another intermediate vector -`P`: a variable that can be used with A*mul*B!        in order to apply the stochastic or sub-stochastic matrix       (column) -`t`: the value of time in the heat kernel $0 <= t$ -`eps`: the solution tolerance $ 0 < eps < 1 $ -`maxiter`: the maximum number of series terms to use

## Returns

-`x`: the result of the stochastic heat kernel evaluation

## Example

```
# TODO Show an example of how to use the expert interface
```
