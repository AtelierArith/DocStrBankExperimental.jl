```
siteinds(tag::String, N::Integer; kwargs...)
```

`tag`のタイプの物理サイトインデックスの配列を`N`作成します。キーワード引数を使用して量子数の保存を指定できます。サポートされているキーワード引数については、サイトタイプ`tag`に対応する`space`関数を参照してください。

# 例

```julia
N = 10
s = siteinds("S=1/2", N; conserve_qns=true)
```
