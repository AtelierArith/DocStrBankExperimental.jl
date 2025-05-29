```
struct FEDomains{A,B}
  domains_res::A
  domains_jac::B
end
```

Fields:

  * `domains_res`: triangulations relative to the residual (nothing by default)
  * `domains_jac`: triangulations relative to the Jacobian (nothing by default)
