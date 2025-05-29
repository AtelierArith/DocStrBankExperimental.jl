```julia
mutable struct ImGuiTest
```

上流の `ImGuiTest` のラッパーです。これを自分で作成しないでください、[`@register_test()`](@ref) を使用してください。作成されたら、これらのプロパティに関数を割り当てることができます：

  * `GuiFunc::Function`、実行/テストしたいスタンドアロンのGUIコード用。自分のGUIをテストしている場合は、これは必要ないはずです。
  * `TestFunc::Function`、実行したいテスト用。

割り当てる関数は、[`TestContext`](@ref) に対して1つの引数を取る必要があります。

!!! danger
    これはメモリ安全でない型です、エンジンが生きている間だけ使用してください。

