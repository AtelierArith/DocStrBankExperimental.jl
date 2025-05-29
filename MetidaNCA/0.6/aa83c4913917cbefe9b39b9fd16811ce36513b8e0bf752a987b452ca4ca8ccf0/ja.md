```
pkplot(data::DataSet{T};
typesort::Union{Nothing, Symbol, AbstractVector{Symbol}} = nothing,
pagesort::Union{Nothing, Symbol, AbstractVector{Symbol}, NoPageSort} = nothing,
filter::Union{Nothing, Dict{Symbol}} = nothing,
uylims::Bool = false,
ldict = nothing,
savepath::Union{Nothing, AbstractString} = nothing,
namepref::Union{Nothing, AbstractString} = nothing,
onlyplots = false,
kwargs...) where T <: AbstractSubject
```

対象セットのPKプロット。

  * `typesort` - このIDキーでページをソートします;
  * `pagesort` - このIDキーで異なるページをソートします;
  * `filter` - フィルターが対象IDの部分集合である場合のみ対象を使用します;
  * `uylims` - すべてのデータセットに同じylimsを使用します;
  * `ldict` - 置き換え用のラベルを持つDict;
  * `savepath` - プロット保存用のパス;
  * `namepref` - ファイル保存用の名前プレフィックス;
  * `onlyplots` - `true`の場合、プロットのベクトルのみを返します;

`pagesort = MetidaNCA.NoPageSort()`を使用してページプロットを防ぎます（単一のプロットを返します）。

ペアのベクトルを返します: `ページID` => `プロット`。
