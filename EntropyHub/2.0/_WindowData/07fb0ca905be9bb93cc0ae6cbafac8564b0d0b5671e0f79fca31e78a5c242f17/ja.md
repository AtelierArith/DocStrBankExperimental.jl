```
WinData, Log = WindowData(Data)
```

`Data` に与えられたシーケンスを、重複のない要素数 floor(N/5) の部分シーケンスのコレクションにウィンドウ化します。最終ウィンドウを満たさない余りの要素は除外されます。`Data` が単変量シーケンス（ベクトル）の場合、`WinData` は 5 つのベクトルのベクトルになります。`Data` が多変量シーケンスの集合（NxM 行列）の場合、各 M 列は N 要素のシーケンスとして扱われ、`WinData` はサイズ [(floor*N,5), M] の 5 つの行列のベクトルになります。`Log` 辞書には、ウィンドウ化プロセスに関する情報が含まれています。これには以下が含まれます：

`DataType`      - `Data` として渡されたデータシーケンスのタイプ

`DataLength`    - `Data` におけるシーケンス要素の数

`WindowLength`  - `WinData` の各ウィンドウ内の要素数

`WindowOverlap` - ウィンドウ間の重複要素の数

`TotalWindows`  - `Data` から抽出されたウィンドウの数

`Mode`          - ウィンドウを満たさない残りのシーケンス要素 (`< WinLen`) を含めるか除外するかの決定。

```
WinData, Log = WindowData(Data::AbstractArray{T} where T<:Real, WinLen::Union{Nothing,Int}=nothing, Overlap::Int=0, Mode::String="exclude")
```

指定されたキーワード引数を使用して、`Data` に与えられたシーケンスを部分シーケンスのコレクションにウィンドウ化します：

# 引数：

`WinLen`  - 各ウィンドウ内の要素数、正の整数 (>10)

`Overlap` - ウィンドウ間の重複要素の数、正の整数 (< WinLen)

`Mode`    - ウィンドウを満たさない残りのシーケンス要素 (`< WinLen`) を含めるか除外するかの決定、文字列 - `"include"` または `"exclude"` のいずれか（デフォルトは `"exclude"`）。

# 参照： `ExampleData`
