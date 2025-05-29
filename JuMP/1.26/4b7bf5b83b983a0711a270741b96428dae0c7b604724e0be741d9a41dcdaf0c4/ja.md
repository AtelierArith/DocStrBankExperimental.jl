```
write_to_file(
    model::GenericModel,
    filename::String;
    format::MOI.FileFormats.FileFormat = MOI.FileFormats.FORMAT_AUTOMATIC,
    kwargs...,
)
```

JuMPモデル`model`を`filename`に`format`形式で書き込みます。

サポートされている形式のリストについては、[`MOI.FileFormats.FileFormat`](@ref)を参照してください。

## 圧縮

ファイル名が`.gz`で終わる場合、ファイルはGZipを使用して圧縮されます。

ファイル名が`.bz2`で終わる場合、ファイルはBZip2を使用して圧縮されます。

## キーワード引数

他の`kwargs`は、選択した形式の`Model`コンストラクタに渡されます。

詳細については、各ファイル形式の`Model`コンストラクタのドキュメントを参照してください。例えば、[`MOI.FileFormats.MPS.Model`](@ref)。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0);

julia> @objective(model, Min, 2 * x + 1);

julia> filename = joinpath(mktempdir(), "model.mps");

julia> write_to_file(model, filename; generic_names = true)

julia> print(read(filename, String))
NAME
ROWS
 N  OBJ
COLUMNS
    C1        OBJ       2
RHS
    rhs       OBJ       -1
RANGES
BOUNDS
 LO bounds    C1        0
 PL bounds    C1
ENDATA
```

## ソルバー特有の形式

[`write_to_file`](@ref)は、ソルバーの選択に依存しないMathOptInterfaceパッケージのJulia関数を呼び出します。つまり、モデルをディスクに書き込むためにソルバーの内部APIを呼び出すことはありません。

特にMPSファイルについては、[`write_to_file`](@ref)はソルバーの内部APIがサポートする機能の全範囲をサポートしていない場合があります。これは、一部のソルバーがMPS形式に対してソルバー特有の拡張を定義しているのに対し、私たちのJulia実装は複数のソルバーにわたって標準化された機能のみをサポートしているためです。

ソルバーの内部APIを使用してファイルをディスクに書き込むには、[`direct_model`](@ref)を使用し、ソルバーのC APIを呼び出します。例えば：

```jldoctest
julia> import HiGHS

julia> model = direct_model(HiGHS.Optimizer());

julia> set_silent(model)

julia> @variable(model, x >= 0);

julia> @objective(model, Min, 2 * x + 1);

julia> filename = joinpath(mktempdir(), "model.mps");

julia> HiGHS.Highs_writeModel(backend(model), filename);

julia> print(read(filename, String))
NAME
ROWS
 N  Obj
COLUMNS
    x         Obj       2
RHS
    RHS_V     Obj       -1
ENDATA
```
