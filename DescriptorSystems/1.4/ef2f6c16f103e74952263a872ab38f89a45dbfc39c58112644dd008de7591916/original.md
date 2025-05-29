```
sys = dss(A, E, B, C, D; Ts = 0, check_reg = false, 
          atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ )
```

Create for `Ts = 0` a descriptor system model `sys = (A-λE,B,C,D)` for a continuous-time state space system of the form

```
Edx(t)/dt = Ax(t) + Bu(t) ,
y(t)      = Cx(t) + Du(t) ,
```

where `x(t)`, `u(t)` and `y(t)` are the system state vector, system input vector and system output vector, respectively,  for the continuous time variable `t`. 

For a nonzero positive sampling time `Ts = ΔT`, the descriptor system model specifies a discrete-time state space system of the form  

```
Ex(t+ΔT) = Ax(t) + Bu(t)
y(t)     = Cx(t) + Du(t)
```

for the discrete values of the time variable `t = 0, ΔT, 2ΔT, ...`.  Use `Ts = -1` if the sampling time is not specified. In this case, by convention  `ΔT = 1`. 

For a system with zero feedthrough matrix `D`, it is possible to set `D = 0` (the scalar zero).  

For a standard state space system, `E` is the identity matrix. In this case, it is possible to set `E = I` (the boolean uniform scaling). Alternatively, use 

```
sys = dss(A, B, C, D; Ts = 0)
```

to create a standard system.

For a system corresponding to a static gain `D`, use

```
sys = dss(D; Ts = 0)
```

It is possible to specify a descriptor system via all or part of its matrices using the form 

```
sys = dss(A = mat1, E = mat2, B = mat3, C = mat4, D = mat5; Ts = 0, check_reg = false, 
          atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ)
```

where `A`, `E`, `B`, `C`, and `D` are keyword parameters set to appropriate matrix values  `mat1`, `mat2`, `mat3`, `mat4`, and `mat5`, respectively. If some of the system matrices are omited, then zero matrices of appropriate sizes are employed instead.  

It is assumed that the pencil `A-λE` is regular (i.e., `det(A-λE) ̸≡ 0`), and therefore, in the interest of efficiency, the regularity of `A-λE` is by default *not* tested. If `check_reg = true`, the regularity of `A-λE` is  additionally checked. In this case, the keyword arguments `atol1`, `atol2` and `rtol` specify, respectively,  the absolute tolerance for the nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance for the nonzero elements of `A` and `E`.   The default relative tolerance is `n*ϵ`, where `n` is the order of the square matrices `A` and `E`, and  `ϵ` is the working machine epsilon.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
