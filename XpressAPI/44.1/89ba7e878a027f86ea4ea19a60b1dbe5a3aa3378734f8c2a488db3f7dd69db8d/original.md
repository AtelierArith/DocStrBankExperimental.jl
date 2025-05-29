```
XPRS_CHOLESKYALG
```

Newton barrier: type of Cholesky factorization used. (integer)

Default value: `-1 (automatic)`

Values are a bitset: bit 0 : matrix blocking: 0: automatic setting; 1: manual setting. bit 1 : if manual selection of matrix blocking: 0: multi-pass; 1: single-pass. bit 2 : nonseparable QP relaxation: 0: off; 1: on. bit 3 : corrector weight: 0: automatic setting; 1: manual setting. bit 4 : if manual selection of corrector weight: 0: off; 1: on. bit 5 : refinement: 0: automatic setting; 1: manual setting. bit 6 : preconditioned conjugate gradient method (PCGM): 0: PCGM off; 1: PCGM on. bit 7 : Preconditioned quasi minimal residual (QMR) to refine solution: 0: QMR off; 1: QMR on. bit 8 : Perform refinement on the augmented system 0: off; 1: on. bit 9 : Force highest accuracy in refinement 0: off; 1: on.
