```
function initialise!(field, value) # dummy function for documentation
    # Assign `value` to field in-place
    nothing
end
```

この関数は、指定された `field` を提供された `value` にインプレースで設定します。シミュレーションを実行する前にフィールドを初期化するのに便利です。

# 入力引数

  * `field` は初期化するフィールドを指定します。フィールドは `AbractScalarField` または `AbstractVectorField` のいずれかでなければなりません。
  * `value` は設定する値を定義します。これは、変更されるフィールドに応じてスカラーまたはベクトル（3成分）である必要があります。例えば、`AbstractVectorField` の場合、`value=[10,0,0]` と指定できます。

注意: ほとんどの場合、変更されるフィールドは物理モデル内に格納されています。すなわち、`Physics` オブジェクトです。したがって、引数 `value` はモデルを完全に指定する必要があります。例えば、`mymodel` という名前の `Physics` モデルを作成して速度フィールド `U` を設定する場合、引数 `field` を `mymodel.momentum.U` に設定します。以下の例を参照してください。

# 例

```julia
initialise!(mymodel.momentum.U, [2.5, 0, 0])
initialise!(mymodel.momentum.p, 1.25)
```
