```
inf_params::InferenceParams
```

抽象解釈に基づく型推論操作を制御するパラメータ。

---

  * `inf_params.max_methods::Int = 3` 型推論は、`max_methods` より多くの一致するメソッドがある場合、呼び出しの分析をあきらめます。これは、コンパイラの待機時間と生成されたコードのパフォーマンスのトレードオフです。通常、多くのメソッドを考慮することは、質の低い型情報を取得するのに*多く*の時間を費やすことを意味するため、このオプションは低く保つべきです。 [`Base.Experimental.@max_methods`](@ref) は、この設定をモジュールごとまたはメソッドごとの注釈ベースでより細かく制御できます。

---

  * `inf_params.max_union_splitting::Int = 4` 一致するメソッドまたは条件付き型のセットを計算する前に、スワップまたは展開する最大のユニオンタプルの数を指定します。

---

  * `inf_params.max_apply_union_enum::Int = 8` `Core._apply_iterate` への呼び出しを推論する際に、スワップまたは展開する最大のユニオンタプルの数を指定します。

---

  * `inf_params.max_tuple_splat::Int = 32` `Core._apply_iterate` への呼び出しを推論しようとする際に、タプルがこの数以上の要素を含む場合、分析を中止します。

---

  * `inf_params.tuple_complexity_limit_depth::Int = 3` 再帰的呼び出しグラフを推論する際に、特化したメソッドシグネチャとして現れることができる大きなタプル型の最大深さを指定します。

---

  * `inf_params.ipo_constant_propagation::Bool = true` `false` の場合、拡張ラティス情報を使用した分析を無効にします。つまり、具体的な評価、半具体的な解釈、および定数伝播を完全に無効にします。 [`Base.@constprop :none`](@ref Base.@constprop) は、この設定をメソッドごとの注釈ベースでより細かく制御できます。

---

  * `inf_params.aggressive_constant_propagation::Bool = false` `true` の場合、拡張ラティス情報が利用可能な場合、すべてのメソッドで定数伝播を強制します。 [`Base.@constprop :aggressive`](@ref Base.@constprop) は、この設定をメソッドごとの注釈ベースでより細かく制御できます。

---

  * `inf_params.unoptimize_throw_blocks::Bool = true` `true` の場合、`throw` することが知られているブロック内の呼び出しの推論をスキップします。これは、一般的な状況でランタイムパフォーマンスを犠牲にすることなく、コンパイラの待機時間を改善する可能性があります。

---

  * `inf_params.assume_bindings_static::Bool = false` `true` の場合、新しいバインディングが追加されないと仮定します。つまり、推論時に存在しないバインディングは、ランタイムで常に存在しないと仮定できます（したがって、例えばそれへのアクセスは `throw` します）。この仮定は、ネイティブコード実行のためのJuliaのセマンティクスでは成り立たないため、デフォルトは `false` です。

---
