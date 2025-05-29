Make a struct of inequality measures. This is mainly taken from chs 5 and 6 of the World Bank book.

1. `rawdata` a matrix with cols with weights and incomes
2. `atkinson_es` inequality aversion values for the Atkinson indexes
3. `generalised_entropy_alphas`
4. `weightpos` - column with weights
5. `incomepos` - column with incomes

Returned is a Dict of inequality measures with:

  * `Gini`;
  * `Atkinson`, for each value in `atkinson_es`;
  * `Theil`;
  * `generalised_entropy`;
  * `Hoover`;
  * `Theil`;
  * `Palma`.

See WB chs 5 an 6, and Cobham and Sumner on the Palma.

Also in the struct are:

  * `total_income`
  * `total_population`
  * `average_income`
  * `deciles`.
