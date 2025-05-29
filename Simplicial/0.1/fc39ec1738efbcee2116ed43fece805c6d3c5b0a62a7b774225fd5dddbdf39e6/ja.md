```
CombinatorialCode{T<:Integer}
```

集合 $[n] = {1,...,n}$ の部分集合のコレクション。コードワードは配列内の `Set{T}` オブジェクトとして保存されます。

# コンストラクタ

```
CombinatorialCode(itr, [vertices=union(itr...)])
```

イテラブルコレクション `itr` のユニークな要素をコードワードとして収集します。オプションの引数 `vertices` は、トリビアルニューロン、すなわち決して発火しないニューロンを作成することを可能にします。頂点は型 `eltype(vertices)` であり、`vertices` が空の場合は型 `TheIntegerType` が使用されます。ワードはそのバイナリベクトル表現によって、グレード付き逆辞書順で保存されます（詳細は [`lessequal_GrRevLex`](@ref) を参照）。

```
CombinatorialCode(B::AbstractMatrix{Bool}; order="rows")
```

行列 `B` の行をコードワードとして解釈します。キーワード引数 `order` は `"rows"` または `"cols"` のいずれかで、`B` の行または列をコードワードとして解釈するかを指定します。`B` が *非常に* 大きくない限り、頂点にはデフォルトで `TheIntegerType` が使用されます。この場合、使用可能な最小の整数型が使用されます。
