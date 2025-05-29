```
filewriter(path::AbstractString, ds::AbstractDataset; [...])
```

`ds`を指定された区切り文字`delimiter`（デフォルトはカンマ）を使用してファイル（`path`）にテキストとして書き込みます。ユーザーは`delimiter`キーワード引数に単一の文字または文字のベクターを渡すことができます。

# キーワード引数

  * `delimiter`: デフォルトでは、`filewriter`はカンマを区切り文字として使用しますが、ユーザーは`delimiter`キーワード引数を介して他の任意の`Char`（または`Char`のベクター）を渡すことができます。
  * `mapformats`: これを`true`に設定すると、`filewriter`はフォーマットされた値を書き込みます。
  * `append`: これを`true`に設定すると、`filewriter`は入力ファイルの末尾に値を追加します。
  * `header`: `filewriter`関数は出力ファイルに列名を書き込みますが、`header = false`を設定することでこれを防ぐことができます。
  * `buffsize`: このオプションはバッファサイズを制御します。
  * `lsize`: このオプションは値を書き込むための行サイズを制御します。
  * `threads`: `true`に設定すると、`filewriter`はすべてのスレッドを活用します。

# 例

```julia
julia> using InMemoryDatasets

julia> ds = Dataset(x=[1.0, 2.1, -2.0], y = 1:3)
3×2 Dataset
 Row │ x         y        
     │ identity  identity 
     │ Float64?  Int64?   
─────┼────────────────────
   1 │      1.0         1
   2 │      2.1         2
   3 │     -2.0         3

julia> filewriter("_tmp.csv", ds)
```
