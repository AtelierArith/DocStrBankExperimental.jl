```
struct FEDomains{A,B}
  domains_res::A
  domains_jac::B
end
```

フィールド:

  * `domains_res`: 残差に対する三角分割（デフォルトでは何もなし）
  * `domains_jac`: ヤコビ行列に対する三角分割（デフォルトでは何もなし）
