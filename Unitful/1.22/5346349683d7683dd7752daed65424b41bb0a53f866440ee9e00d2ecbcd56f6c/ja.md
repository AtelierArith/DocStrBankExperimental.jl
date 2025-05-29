```
@dimension(symb, abbr, name, autodocs=false)
```

新しい次元を作成します。`name` は [`Unitful.Dimension`](@ref) オブジェクトの型パラメータ内で識別子のように使用されます。`symb` はこのマクロが呼び出される名前空間で定義されたシンボルで、[`Unitful.Dimensions`](@ref) オブジェクトにバインドされます。ほとんどの目的において、ユーザーが次元分析を行う際に操作するのはこのオブジェクトです。シンボルはエクスポートされません。

このマクロは [`Unitful.abbr`](@ref) を拡張し、文字列 `abbr` を使用して新しい次元を省略形式で表示します。

ユーザーが新しく定義された次元の [`Unitful.Quantity`](@ref)、[`Unitful.Level`](@ref)、および [`Unitful.Units`](@ref) オブジェクトにディスパッチできるようにする型エイリアスが作成されます。量やレベルの型エイリアスは単に `name` で与えられ、単位の型エイリアスは `name*"Units"` で与えられます。例えば、`LengthUnits` です。長さ次元に対して `FreeUnits` にディスパッチするためのエイリアスである `LengthFreeUnits` もあります。エイリアスはエクスポートされません。`autodocs == true` の場合、これらのエイリアスのためにドキュメント文字列が自動的に生成されます。

!!! compat "Unitful 1.10"
    `@dimension` 呼び出しの前にドキュメント文字列を追加して結果の次元シンボルを文書化するには、Unitful 1.10 以降が必要です。`autodocs` 引数も Unitful 1.10 以降が必要です。


最後に、[`@dimension`](@ref) で新しい次元を定義する場合、その次元のために [`Unitful.preferunits`](@ref) で好ましい単位を指定する必要があります。そうしないと、その次元でのプロモーションは機能しません。これは [`@refunit`](@ref) マクロ内で自動的に行われます。

`symb` がバインドされている `Dimensions` オブジェクトを返します。

`src/pkgdefaults.jl` からの使用例: `@dimension 𝐋 "𝐋" Length`
