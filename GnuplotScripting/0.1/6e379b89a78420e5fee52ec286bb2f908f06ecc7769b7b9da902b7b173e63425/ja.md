```julia
register_data(gp::GnuplotScript,
              data::AbstractVecOrMat;
              copy_data::Bool=true) -> id
```

データを登録し、関連するデータ識別子を返します。登録されたデータはプロットスクリプトファイルに埋め込まれます。返される `id` は登録されたデータを参照するために使用されます。

# 使用例

```julia
gp = GnuplotScript()

M = rand(10,3)

id = register_data(gp, M)

free_form(gp,"replot $id u 1:2")
free_form(gp,"replot $id u 1:3")
```
