```
GSympNet(d)
```

次元 $d$ の $G$-SympNet を作成します。

[`DataLoader`](@ref) のインスタンスを供給することで呼び出すことができる追加のコンストラクタが存在します（このコンストラクタの使用例については [`LASympNet`](@ref) を参照してください）。

# 引数

キーワード引数は次のとおりです：

  * `upscaling_dimension::Int = 2d`: 勾配層の *アップスケーリング次元*。詳細については [`GradientLayerQ`](@ref) と [`GradientLayerP`](@ref) のドキュメントを参照してください。
  * `n_layers::Int2`: 層の数（すなわち、[`GradientLayerQ`](@ref) と [`GradientLayerP`](@ref) の合計数）。
  * `activationtanh`: 適用される活性化関数。
  * `init_upper::Booltrue`: 勾配層を初期化して、最初に $q$-成分を修正するようにします。
