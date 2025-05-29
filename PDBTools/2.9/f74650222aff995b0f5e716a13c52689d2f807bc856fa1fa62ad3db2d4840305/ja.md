```
write_pdb(filename::String, atoms::AbstractVector{<:Atom}, [selection]; header=:auto, footer=:auto, append=false)
```

`atoms`の原子を`filename`にPDBファイルとして書き込みます。`selection`引数は、`atoms`の原子のサブセットを選択するために使用できる文字列です。例えば、`write_pdb("test.pdb", atoms, "name CA")`のように使用します。

# 引数

  * `filename::String`: 書き込むファイルの名前。
  * `atoms::AbstractVector{<:Atom}`: ファイルに書き込む原子。

# オプションの位置引数

  * `selection::String`: `atoms`の原子のサブセットを選択するための選択文字列。

# キーワード引数

  * `header::Union{String, Nothing}=:auto`: PDBファイルに追加するヘッダー。`:auto`の場合、`atoms`の原子の数を含むヘッダーが追加されます。
  * `footer::Union{String, Nothing}=:auto`: PDBファイルに追加するフッター。`:auto`の場合、"END"キーワードを含むフッターが追加されます。
  * `append::Bool=false`: `true`の場合、原子はファイルに追加され、上書きされることはありません。

!!! compat
    `append`キーワード引数はPDBTools.jl v2.7.0以降で利用可能です。

