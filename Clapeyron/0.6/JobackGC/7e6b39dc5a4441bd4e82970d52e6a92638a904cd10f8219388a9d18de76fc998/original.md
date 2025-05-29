```
JobackGC
```

Module containing group contribution calculations using the joback method. the available functions are:

  * `JobackGC.T_c(model::JobackModel)`: critical temperature (in K)
  * `JobackGC.P_c(model::JobackModel)`: critical pressure (in Pa)
  * `JobackGC.V_c(model::JobackModel)`: critical volume (in m3/mol)
  * `JobackGC.T_b(model::JobackModel)`: normal boiling point (in K)
  * `JobackGC.H_form(model::JobackModel)`: enthalpy of formation at 298K, ideal gas (in J/mol)
  * `JobackGC.G_form(model::JobackModel)`: gibbs energy of formation at 298K, ideal gas (in J/mol)
  * `JobackGC.S_form(model::JobackModel)`: entropy of formation at 298K, ideal gas (in J/mol/K)
  * `JobackGC.H_fusion(model::JobackModel)`: enthalpy of fusion (in J/mol, at 1 atm)
  * `JobackGC.H_vap(model::JobackModel)`: molar enthalpy of vaporization (in J/mol, at normal boiling point)
  * `JobackGC.C_p(model::JobackModel, T)`: ideal gas isobaric heat capacity (in J/mol/K)
  * `JobackGC.Visc(model::JobackModel, T)`: liquid dynamic viscocity (in Pa*s)
