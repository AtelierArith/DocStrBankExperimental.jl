```
HEOMSuperOp(op, opParity, refADOs; Id_cache=I(refADOs.N))
```

与えられたシステムスーパーオペレーターに対応するHEOMスーパーオペレーター行列を構築します。このスーパーオペレーターはすべての`ADOs`に作用します。

すべての`ADOs`に対する乗算中に、出力`ADOs`のパリティは、このHEOMスーパーオペレーターのパリティに依存して変わる可能性があります。

# パラメータ

  * `op` : すべての`ADOs`に作用するシステムスーパーオペレーター。
  * `opParity::AbstractParity` : 与えられたオペレーター（`op`）のパリティラベルで、`EVEN`または`ODD`である必要があります。
  * `refADOs::ADOs` : この参照`ADOs`からシステムの`dimensions`と`ADOs`の数（`N`）をコピーします。
