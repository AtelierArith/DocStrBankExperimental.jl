```
xy_flash(model,spec::FlashSpecifications,z,w0::FlashResult,method::GeneralizedXYFlash)
xy_flash(model,spec::FlashSpecifications,z,w0::FlashResult;rtol = 1e-12,atol = 1e-10,max_iters = 50)
```

Routine to solve a non-reactive multiphase, multicomponent flash problem with arbitrary specifications. Based on the unified formulation proposed by Ben Gharbia (2021). The two necessary specifications are taken from `specs`, the initial point is obtained from `w0`. Returns a [`FlashResult`](@ref) struct containing molar fractions, vapour fractions, molar volumes and the equilibrium temperature and pressure.

## Examples

```
spec = FlashSpecifications(p = 101325.0, T = 200.15) #p-T flash
model = cPR(["ethane","propane"],idealmodel=ReidIdeal)
z = [0.5,0.5] #bulk composition
x1 = [0.25,0.75] #liquid composition
x2 = [0.75,0.25] #gas composition
compositions = [x1,x2]
volumes = [6.44e-5,0.016]
fractions = [0.5,0.5]
p0,T0 = NaN,NaN #in p-T flash, pressure and temperature are already specifications
data = FlashData(p0,T0)
result0 = FlashResult(compositions,fractions,volumes,data) #a FlashResult containing all necessary information
result = xy_flash(model,spec,z,result) #perform the flash
```
