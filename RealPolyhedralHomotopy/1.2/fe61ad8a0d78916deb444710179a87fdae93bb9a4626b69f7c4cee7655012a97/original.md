```
certify_patchwork(F::System; Number_Real_Solutions = false)
```

Certify if a given system is patchworked that all real solutions can be found using the real polyhedral homotopy. It returns the value `1` if the system `F` is certified to be patchworked according to the certification inequality.  Otherwise, `0` is returned. 

# Arguments

  * `F` : The target system for the real polyhedral homotopy.

```julia
@var x y;
F = System([-1 - 24000*y + x^3, -9 + 50*x*y - 1*y^2]);
result = certify_patchwork(F)
```

```
1
```

  * There is an option `Number_Real_Solutions` returning `(1,k)` where `k` is number of real solutions to the target system when the target system is patchedworked. The default value for the option is false.

```julia
result = certify_patchwork(F; Number_Real_Solutions = true)
```

```
(1,4)
```
