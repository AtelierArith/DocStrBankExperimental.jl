```
witharray(f, v::CeedVector, mtype=MEM_HOST)
```

`CeedVector` `v`のデータを含む配列で`f`を呼び出します。 [`memory type`](@ref MemType) `mtype`を使用します。

クロージャに関するパフォーマンスの問題のため、`f`が複雑な操作である場合、マクロバージョン`@witharray`を使用する方が効率的である可能性があります（[Juliaドキュメント](https://docs.julialang.org/en/v1/manual/performance-tips)の「キャプチャされた変数のパフォーマンス」に関するセクションおよび関連する[GitHubの問題](https://github.com/JuliaLang/julia/issues/15276)を参照）。

# 例

ベクトルの合計を返す：

```
witharray(sum, v)
```
