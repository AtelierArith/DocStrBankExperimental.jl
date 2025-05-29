This is a Workers. Each field is an array which stores the values for all the workers in the economy. Note that the `O_h` field is an integer, while the rest are floats.

For all fields the entry at index `i` corresponds to the `i`th worker.

# Fields

  * `Y_h`: Net disposable income of worker owner (investor)
  * `D_h`: Deposits
  * `K_h`: Capital stock
  * `w_h`: Wages (0 if inactive or unemployed)
  * `O_h`: Occupation (0 if unemployed, -1 if inactive)
  * `C_d_h`: Consumption budget
  * `I_d_h`: Investment budget
  * `C_h`: Realised consumption
  * `I_h`: Realised investment
