```
find_missing_sums(missed,de::MeanfieldEquations)
```

初期の平均の微分方程式のセットから、欠落しているすべての平均を見つけ、シンボリックな和の中に配置します。欠落している平均が方程式で使用されている和のインデックスの1つを含む場合、[`Index`](@ref)はキーワード引数`extra_indices`に従って交換されます。[`find_missing`](@ref)を使用します。

# 引数

*`missed`: このメソッドを呼び出す前に欠落している平均を表す初期の平均のベクトル。 *`de`: 欠落している平均が検索される方程式のセット。

# オプションの引数

*`extra_indices`: 欠落している項を見つける過程で必要とされ、作成される追加の[`Index`](@ref)エンティティを表すシンボルのベクトル。この引数は、Meanfield-Equationsの次数が1を超える場合に必要であり、与えられたシンボルの数は対応する次数と一致しなければなりません。 *`checking`: アルゴリズムが見つかった平均を`missed`ベクトルに追加する前に、随伴値と重複をチェックするかどうかを定義するBool。 *`scaling`: 平均が`missed`ベクトルに追加される方法を定義するBool。trueの場合、演算子（インデックスなし）がすでに`missed`ベクトルに含まれていない平均のみが追加されます。

参照: [`find_missing`](@ref), [`indexed_meanfield`](@ref), [`meanfield`](@ref), [`find_missing_sums`](@ref)
