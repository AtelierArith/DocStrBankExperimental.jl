This is a Firms type. Each field is an array which stores the values for all the firms in the economy. Note that the `G_i`, `N_i` and `V_i` fields are integers, while the rest are floats.

For all fields the entry at index `i` corresponds to the `i`th firm.

# Fields

  * `G_i`: Principal product
  * `alpha_bar_i`: Average productivity of labor
  * `beta_i`: Productivity of intermediate consumption
  * `kappa_i`: Productivity of capital
  * `w_i`: Wages
  * `w_bar_i`: Average wage rate
  * `delta_i`: Depreciation rate for capital
  * `tau_Y_i`: Net tax rate on products
  * `tau_K_i`: Net tax rate on production
  * `N_i`: Number of persons employed
  * `Y_i`: Production of goods
  * `Q_i`: Sales of goods
  * `Q_d_i`: Demand for goods
  * `P_i`: Price
  * `S_i`: Inventories
  * `K_i`: Capital, in real terms
  * `M_i`: Intermediate goods/services and raw materials, in real terms
  * `L_i`: Outstanding loans
  * `pi_bar_i`: Operating margin
  * `D_i`: Deposits of the firm
  * `Pi_i`: Profits
  * `V_i`: Vacancies
  * `I_i`: Investments
  * `E_i`: Equity
  * `P_bar_i`: Price index
  * `P_CF_i`: Price index
  * `DS_i`: Differnece in stock of final goods
  * `DM_i`: Difference in stock of intermediate goods
  * `DL_i`: Obtained loans
  * `DL_d_i`: Target loans
  * `K_e_i`: Expected capital
  * `L_e_i`: Expected loans
  * `Q_s_i`: Expected sales
  * `I_d_i`: Desired investments
  * `DM_d_i`: Desired materials
  * `N_d_i`: Desired employment
  * `Pi_e_i`: Expected profits

### Household fields (firms' owners)

  * `Y_h`: Net disposable income of firm owner (investor)
  * `C_d_h`: Consumption budget
  * `I_d_h`: Investment budget
  * `C_h`: Realised consumption
  * `I_h`: Realised investment
  * `K_h`: Capital stock
  * `D_h`: Deposits of the owner of the firms
