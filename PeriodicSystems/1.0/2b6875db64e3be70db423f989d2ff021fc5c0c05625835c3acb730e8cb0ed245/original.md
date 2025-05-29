```
ps([PMT::Type,] A::PM1, B::PM2, C::PM3, D::PM4) -> psys::PeriodicStateSpace
```

Construct a `PeriodicStateSpace` object from a quadruple of periodic matrix objects. 

The periodic matrix objects `A`, `B`, `C`, `D` specifies the periodic matrices `A(t)`, `B(t)`, `C(t)` and `D(t)` of a linear periodic time-varying state space model in the continuous-time form

```
 dx(t)/dt = A(t)x(t) + B(t)u(t) ,
 y(t)     = C(t)x(t) + D(t)u(t) ,
```

or in the discrete-time form

```
 x(t+1)  = A(t)x(t) + B(t)u(t) ,
 y(t)    = C(t)x(t) + D(t)u(t) ,
```

where `x(t)`, `u(t)` and `y(t)` are the system state vector,  system input vector and system output vector, respectively,  and `t` is the continuous or discrete time variable.  The system matrices satisfy `A(t) = A(t+T₁)`, `B(t) = B(t+T₂)`, `C(t) = C(t+T₃)`, `D(t) = D(t+T₄)`,   i.e., are periodic with periods `T₁`, `T₂`, `T₃` and `T₄`, respectively.  The different periods must be commensurate (i.e., their ratios must be rational numbers with numerators and denominators up to at most 4 decimal digits).  The periodic matrix objects `A`, `B`, `C`, `D` can have different types `PM1`, `PM2`, `PM3`, `PM4`, respectively, where for a contiuous-time system  `PM1`, `PM2`, `PM3`, `PM4` must be one of the supported continuous-time periodic matrix types, i.e.,  `PeriodicFunctionMatrix`, `PeriodicSymbolicMatrix`, `HarmonicArray`, `FourierFunctionMatrix` or `PeriodicTimeSeriesMatrix`, while for a discrete-time system  `PM1`, `PM2`, `PM3`, `PM4` must be one of the supported discrete-time periodic matrix types, i.e.,  `PeriodicMatrix` or `PeriodicArray`.   Any of the objects `A`, `B`, `C`, `D` can be also specified as a real matrix or vector of appropriate size. 

If `PMT` is not specified, the resulting `psys` has periodic matrices of the same type `PT`, such that `PT` is either the common type of all matrix objects or `PT = PeriodicFunctionMatrix` for a continuous-time system or  `PT = PeriodicMatrix` for a discrete-time system.  If `PMT` is specified, the resulting `psys` has periodic matrices of the same type `PMT`. 

Other convenience constructors are implemented as follows: 

```
ps([PMT::Type,] A, B, C) -> psys::PeriodicStateSpace
```

to construct a `PeriodicStateSpace` object for a quadruple of the form `(A,B,C,0)`;

```
ps(D) -> psys::PeriodicStateSpace
```

to construct a `PeriodicStateSpace` object for a quadruple of the form `([],[],[],D)`;

```
ps([PMT::Type,] A, B, C, D, period) -> psys::PeriodicStateSpace
```

to construct a `PeriodicStateSpace` object with a desired `period` for a quadruple `(A,B,C,D)`; all objects `A`, `B`, `C`, `D` can be also specified as real matrices or vectors of appropriate sizes. 

```
ps([PMT::Type,] A, B, C, period) -> psys::PeriodicStateSpace
```

to construct a `PeriodicStateSpace` object with a desired `period` for a quadruple `(A,B,C,0)`; all objects `A`, `B`, `C` can be also specified as real matrices or vectors of appropriate sizes. 

```
ps(sys::DescriptorStateSpace, period) -> psys::PeriodicStateSpace
```

to construct a `PeriodicStateSpace` object with a desired `period` for a quadruple `(sys.A,sys.B,sys.C,sys.D)` (`sys.E = I` is assumed).
