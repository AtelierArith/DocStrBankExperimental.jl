Linearized 'DC' power flow Model with polar voltage variables.

This model is a basic linear active-power-only approximation, which uses branch susceptance values `br_b = -br_x / (br_x^2 + br_x^2)` for determining the network phase angles.  Furthermore, transformer parameters such as tap ratios and phase shifts are not considered as part of this model.

It is important to note that it is also common for active-power-only approximations to use `1/br_x` for determining the network phase angles, instead of the `br_b` value that is used here.  Small discrepancies in solutions should be expected when comparing active-power-only approximations across multiple tools.

```
@ARTICLE{4956966,
  author={B. Stott and J. Jardim and O. Alsac},
  journal={IEEE Transactions on Power Systems},
  title={DC Power Flow Revisited},
  year={2009},
  month={Aug},
  volume={24},
  number={3},
  pages={1290-1300},
  doi={10.1109/TPWRS.2009.2021235},
  ISSN={0885-8950}
}
```
