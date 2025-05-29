```
make_tokenizer(
    machine::TokenizerMachine;
    tokens::Tuple{E, AbstractVector{E}}= [ integers ],
    goto=true, version=1
) where E
```

評価されると `Base.iterate(::Tokenizer{E, D, $version})` を定義するコードを作成します。`tokens` は次のタプルです：

  * トークン化できないデータに対して発行されるエラートークン、および
  * `machine.n_tokens` の長さを持つ非エラーのトークンのベクター。

ほとんどのユーザーは、より便利なメソッド `make_tokenizer(tokens)` を使用するべきです。

# 使用例

```jldoctest
julia> machine = compile([re"a", re"b"]);

julia> make_tokenizer(machine; tokens=(0x00, [0x01, 0x02])) |> eval

julia> iter = tokenize(UInt8, "abxxxba"); typeof(iter)
Tokenizer{UInt8, String, 1}

julia> collect(iter)
5-element Vector{Tuple{Int64, Int32, UInt8}}:
 (1, 1, 0x01)
 (2, 1, 0x02)
 (3, 3, 0x00)
 (6, 1, 0x02)
 (7, 1, 0x01)
```

入力正規表現内のアクションは無視されます。

`goto`（デフォルト）の場合、より高速ですが、より複雑なゴートコードジェネレーターを使用します。 `version` 番号は `Tokenizer` の最後のパラメータを設定し、同じ要素タイプの異なるトークン化器を作成できるようにします。

参照： [`Tokenizer`](@ref), [`tokenize`](@ref), [`compile`](@ref)
