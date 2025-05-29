```
HEOMSuperOp(op, opParity, refHEOMLS; Id_cache=I(refHEOMLS.N))
```

与えられたシステムスーパーオペレーターに対応するHEOMスーパーオペレーター行列を構築します。このスーパーオペレーターはすべての`ADO`に作用します。

すべての`ADO`に対する乗算中に、出力`ADO`のパリティは、このHEOMスーパーオペレーターのパリティに依存して変わる可能性があります。

# パラメータ

  * `op` : すべての`ADO`に作用するシステムスーパーオペレーター。
  * `opParity::AbstractParity` : 与えられたオペレーター（`op`）のパリティラベルで、`EVEN`または`ODD`である必要があります。
  * `refHEOMLS::AbstractHEOMLSMatrix` : この参照HEOMLS行列からシステムの`dimensions`と`ADO`の数（`N`）をコピーします。
