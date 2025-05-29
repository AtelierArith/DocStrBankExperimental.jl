```
AbstractSimData
```

シミュレーションデータオブジェクトのスーパークラス。これには、[`GridData`](@ref)、[`SimSettings`](@ref) およびシミュレーションを実行するために必要な他のオブジェクトが含まれ、ルール内から必要とされる可能性があります。

`AbstractSimData` オブジェクトは、[`applyrule`](@ref) の最初のパラメータとしてアクセス可能です。

複数のグリッドは、任意の場所から読み取る必要がある場合に、そのキーを使用してインデックスを付けることができます：

```julia
funciton applyrule(data::AbstractSimData, rule::SomeRule{Tuple{A,B}},W}, (a, b), I) where {A,B,W}
    grid_a = data[A]
    grid_b = data[B]
    ...
end
```

単一グリッドシミュレーションでは、`AbstractSimData` オブジェクトは `Matrix` のように直接インデックスを付けることができます。

## メソッド

  * `currentframe(data)`: 現在のフレーム番号を取得します。`Int` 型です。
  * `currenttime(data)`: 現在のフレーム時間を取得します。これは `isa eltype(tspan)` です。
  * `aux(data, args...)`: `aux` データ `NamedTuple` または `Nothing` を取得します。`Symbol` または `Val{:symbol}` 引数を追加すると、aux のフィールドを取得できます。
  * `tspan(data)`: シミュレーションの時間範囲を取得します。`AbstractRange` 型です。
  * `timestep(data)`: シミュレーションの時間ステップを取得します。
  * `boundary(data)`: [`BoundaryCondition`](@ref) を返します - `Remove` または `Wrap`。
  * `padval(data)`: グリッドの境界パディングとして使用する値を返します。

これらも利用可能ですが、使用しない方が良いでしょう。これらの動作は将来のバージョンで保証されていません。これらを使用すると、ルールは特定のコンテキストでのみ有用であることを意味し、推奨されません。

  * `settings(data)`: シミュレーションの [`SimSettings`](@ref) オブジェクトを取得します。
  * `extent(data)`: シミュレーションの [`AbstractExtent`](@ref) オブジェクトを取得します。
  * `init(data)`: シミュレーションの初期 `AbstractArray`/`NamedTuple` を取得します。
  * `mask(data)`: シミュレーションマスク `AbstractArray` を取得します。
  * `source(data)`: 読み取られている `source` グリッドを取得します。
  * `dest(data)`: 書き込まれている `dest` グリッドを取得します。
  * `radius(data)`: グリッドで使用される `Int` 半径を返します。これは境界パディングの量でもあります。
