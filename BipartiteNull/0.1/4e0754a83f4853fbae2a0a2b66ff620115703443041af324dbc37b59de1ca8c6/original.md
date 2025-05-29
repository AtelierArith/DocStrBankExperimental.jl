`CoinTest(pvalue::Float64,testnumber::Int)`

Test Coin function.

# Argument

  * `pvalue`:Probability of true output(greater than 0 but less than 1).Please enter the value to one decimal place or two decimal places.
  * `testnumber`:Test number.

# Return

  * `Bool`:The frequency of true is theoretically close to pvalue.

# Example

using BipartiteNull;

CoinTest(0.5,100000)
