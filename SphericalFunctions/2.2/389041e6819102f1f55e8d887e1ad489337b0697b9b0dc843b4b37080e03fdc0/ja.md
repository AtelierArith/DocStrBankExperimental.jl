```
sYlm_iterator(Y, ℓₘₐₓ, [ℓₘᵢₙ, [iₘᵢₙ]])
```

`Y`の部分ベクトルを返すイテレータを構築します。各部分ベクトルは、$ℓ$が`ℓₘᵢₙ`から`ℓₘₐₓ`までの範囲で、要素$(ℓ,-ℓ)$から$(ℓ,ℓ)$で構成されます。

返されるオブジェクトは元の`Y`データへの*ビュー*であるため、その値を変更することができます。

結果は特定の$ℓ$値に制限されたベクトルであるため、$(ℓ, m)$要素には`[ℓ+m+1]`としてインデックスを付けることができます。例えば、次のように使用することができます。

```
for (ℓ, Yˡ) in zip(ℓₘᵢₙ:ℓₘₐₓ, sYlm_iterator(Y, ℓₘₐₓ))
    for m in -ℓ:ℓ
        Yˡ[ℓ+m+1]  # ... Yˡを使って何かをする
    end
end
```

デフォルトでは、`Y`はすべての可能な値を含むものと仮定され、最初は`(0,0)`から始まります。しかし、`ℓₘᵢₙ`が0でない場合、これは曖昧になる可能性があります：`Y`は本当に`(0,0)`要素から始まり、単にイテレーションを高い位置から始めることを求めているのか？それとも、`Y`は低い`ℓ`値のデータを含んでいないのか？これを解決するために、`iₘᵢₙ`を使用します。これは`Y`における`ℓₘᵢₙ`のインデックスを示します。デフォルトでは、最初のケースを仮定し、`iₘᵢₙ=Ysize(ℓₘᵢₙ-1)+1`と設定します。しかし、`Y`が`ℓₘᵢₙ`未満のデータを含まない場合、`iₘᵢₙ=1`を使用して、$(ℓₘᵢₙ,-ℓₘᵢₙ)$を見つけるための`Y`内のインデックスを示すことができます。

また、インスタンス化時やイテレーション中に境界チェックは行われないことに注意してください。`Y`のサイズと`ℓₘₐₓ`、`ℓₘᵢₙ`、`iₘᵢₙ`の値が意味を持つことを確認するのはあなたの責任です。 ```
