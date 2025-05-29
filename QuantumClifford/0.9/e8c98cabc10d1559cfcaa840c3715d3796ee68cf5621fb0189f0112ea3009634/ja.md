```julia
bigram(
    state::QuantumClifford.AbstractStabilizer;
    clip
) -> Matrix{Int64}

```

テーブルのビグラムを取得します。

これは、クリップされたゲージのテーブルのエンドポイントのリストです。

`clip=true`（デフォルト）である場合、テーブルはビグラムを計算する前にインプレースでクリップされたゲージに変換されます。そうでない場合、クリップゲージの変換はスキップされます（入力がすでに正しいゲージにあることが知られている場合）。

[nahum2017quantum](@cite)で導入され、[li2019measurement](@cite)および[gullans2021quantum](@cite)でアルゴリズムの詳細な説明があります。

関連項目: [`canonicalize_clip!`](@ref)
