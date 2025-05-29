```
min_max_speed_chen_noelle(u_ll, u_rr, orientation::Integer,
                          equations::ShallowWaterEquations1D)
```

ChenとNoelleによる静水再構成のために使用されるHLL型数値フラックスの近似速度。彼らが論文で述べているように、これらの速度は数値フラックスのために選ばれ、正の値を保証し、エントロピー不等式を満たすようにしています。

この静水再構成とその動機に関する詳細は以下にあります。

  * Guoxian Chen and Sebastian Noelle (2017) A new hydrostatic reconstruction scheme based on subcell reconstructions [DOI:10.1137/15M1053074](https://dx.doi.org/10.1137/15M1053074)
