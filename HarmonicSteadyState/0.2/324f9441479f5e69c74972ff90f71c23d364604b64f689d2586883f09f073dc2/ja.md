```
attractors(res::Result{D}; class="stable", not_class=[]) where D
```

[`Result`](@ref) オブジェクトからアトラクタを抽出します。各辞書がブランチ識別子をアトラクタにマッピングする辞書の配列を返します。アトラクタは対応するクラスによってフィルタリングされます。

# キーワード引数

クラスの選択は、`String` または `Vector{String}` を kwarg として渡すことで行います：

```
class::String       :   このクラスの解のみをカウントする ("all" --> すべてをプロット)
not_class::String   :   このクラスの解をカウントしない
```

# 返り値

`Array{Dict,D}`: 各パラメータ値で安定性基準を満たす点にブランチインデックスをマッピングする辞書のベクター
