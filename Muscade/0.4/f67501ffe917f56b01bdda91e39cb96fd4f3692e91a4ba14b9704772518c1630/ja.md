```
Muscade.draw(ElementType,axe,o, Λ,X,U,A,t,SP,dbg;kwargs...)
```

入力は次のとおりです：

  * `ElementType`、この `DataType` に基づいてメソッドがディスパッチされる必要があります。
  * `axe`、`GLMakie` の軸
  * `o`、要素オブジェクトの `AbstractVector`、長さ `nel`
  * `Λ`、サイズ `(nXdof,nel)` の行列
  * `X`、サイズ `(nXdof,nel)` の行列の `NTuple`
  * `U`、サイズ `(nUdof,nel)` の行列の `NTuple`
  * `A`、サイズ `(nAdof,nel)` の行列
  * `t`、時間
  * `SP`、ソルバーパラメータ
  * `dbg`、デバッグ情報
  * `kwargs`、ユーザーが提供したキーワード引数を含む `NamedTuple`。 [`default`](@ref) を参照してください。

参照： [`lagrangian`](@ref)、[`residual`](@ref)、[`doflist`](@ref)
