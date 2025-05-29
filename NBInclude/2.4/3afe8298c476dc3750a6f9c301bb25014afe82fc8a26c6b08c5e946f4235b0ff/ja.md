```
@nbinclude(path::AbstractString; renumber::Bool=false, counters=1:typemax(Int), regex::Regex=r"", anshook = identity, softscope::Bool = false)
```

`path`で指定されたIJulia Jupyterノートブックを含め、ファイルに表示される順序でコードセルを実行し、最後のコードセルの最後の式の結果を返します。

`.jl`ファイルの`include(path)`と同様に、`path`は現在のファイルのパス（存在する場合）に対して相対的であり、`include`や`nbinclude`のネストされた呼び出しはノートブックファイルのパスに対して相対的です。

ノートブックの`N`-番目の入力セルのコードでは、`@__FILE__`マクロ（およびファイル名を使用する他のコード、例：例外のバックトレース）は`path:In[N]`を返します。ここで、`N`はノートブックに保存されたセル番号です。セルに番号がない場合（例：まだ評価されていない場合）、そのセルには`+N`という番号が割り当てられます。`renumber`が`true`に設定されている場合、ノートブックに保存されたセル番号は無視され、各セルには連続した番号`N`が割り当てられます。

`counters`と`regex`を使用して、ノートブックセルのサブセットのみを含めることができます。`counter ∈ counters`が成り立ち、セルのテキストが`regex`に一致するセルのみが実行されます。例えば、

```
@nbinclude("notebook.ipynb"; counters = 1:10, regex=r"# *exec"i)
```

は、セルのテキストに`# exec`や`# ExecuteMe`のようなコメントを含む"notebook.ipynb"の1から10のセルを含めます。

`anshook`は、セルで返されたすべての値に対して関数を実行するために使用できます。

`softscope`は、READMEに記載されている「ハード」および「ソフト」スコープルールの間で切り替えます。

指定されたモジュールにノートブックを含めるには、`nbinclude(module, path; ...)`も参照してください。
