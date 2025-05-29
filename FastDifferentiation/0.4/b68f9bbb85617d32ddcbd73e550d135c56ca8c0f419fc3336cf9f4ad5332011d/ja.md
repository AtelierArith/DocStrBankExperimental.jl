```
jacobian_times_v(
    terms::AbstractVector{<:Node},
    partial_variables::AbstractVector{<:Node}
)
```

`Jv`の象徴的な形の各要素を持つNodeのベクトルを返します。また、`v`変数のベクトルである`v_vector`も返します。これは、`Jv`を評価する関数を生成したい場合や、関数への入力と`v`変数を分けたい場合に便利です。
