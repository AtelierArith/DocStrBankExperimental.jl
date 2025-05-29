```
Maxout(layers...)
Maxout(; layers...)
Maxout(f::Function, n_alts::Int)
```

これは内部層の数を含み、それぞれが同じ入力を受け取ります。その出力は、内部層の出力の要素ごとの最大値です。

線形密な層に対するMaxoutは、普遍近似定理を満たします [goodfellow2013maxout](@cite)。

他の演算子と一緒に削減するには、[`Parallel`](@ref)も参照してください。

## 引数

  * 層は3つの形式で指定できます：

      * `N`個のLux層のリスト
      * `N`個のキーワード引数として指定
      * 引数なしの関数`f`と、層の数を指定する整数`n_alts`

# 拡張ヘルプ

## 入力

  * `x`: 各層に渡される入力

## 戻り値

  * 出力は、各個別層の出力の要素ごとの`max`を取ることで計算されます。
  * `layers`の更新された状態

## パラメータ

  * 各`layer`のパラメータは、`fields = layer_1, layer_2, ..., layer_N`のNamedTupleでラップされます（kwargs APIを使用する場合、名前が変更されます）

## 状態

  * 各`layer`の状態は、`fields = layer_1, layer_2, ..., layer_N`のNamedTupleでラップされます（kwargs APIを使用する場合、名前が変更されます）

```
