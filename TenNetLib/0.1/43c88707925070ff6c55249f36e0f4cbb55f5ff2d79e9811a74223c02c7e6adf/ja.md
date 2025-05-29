```
function product(env::LinkTensorsTTN, psi::TTN, v::ITensor)::ITensor
```

入力 `v` を持つ環境テンソルの積を返します。収束は `psi` の直交中心で行われます。
