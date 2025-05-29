```
v = cfvariable(ds::NCDataset,varname::SymbolOrString; <attrib> = <value>)
```

データセット `ds` から変数 `varname` を `NCDataset.CFVariable` として返します。キーワード引数 `<attrib>` は CF 規約に関連する属性（`fillvalue`、`missing_value`、`scale_factor`、`add_offset`、`units`、および `calendar`）です。これらの属性の値を指定することで、データセットに指定された値を上書きすることができます。属性が `nothing` に設定されている場合、その属性は読み込まれず、対応する変換は無視されます。この関数は、いくつかの変数属性を上書きできる追加の柔軟性を持つ `ds[varname]` に似ています。

例:

```julia
NCDataset("foo.nc","c") do ds
  defVar(ds,"data",[10., 11., 12., 13.], ("time",), attrib = Dict(
      "add_offset" => 10.,
      "scale_factor" => 0.2))
end

# 保存された（パックされた）値は [0., 5., 10., 15.]
# これは 0.2 .* [0., 5., 10., 15.] .+ 10 が [10., 11., 12., 13.] になるためです。

ds = NCDataset("foo.nc");

@show ds["data"].var[:]
# [0., 5., 10., 15.] を返します。

@show cfvariable(ds,"data")[:]
# [10., 11., 12., 13.] を返します。

# add_offset も scale_factor も適用されません
@show cfvariable(ds,"data", add_offset = nothing, scale_factor = nothing)[:]
# [0, 5, 10, 15] を返します。

# add_offset は適用されますが、scale_factor は適用されません
@show cfvariable(ds,"data", scale_factor = nothing)[:]
# [10, 15, 20, 25] を返します。

# 0 がフィル値として宣言されます（add_offset と scale_factor は通常通り適用されます）
@show cfvariable(ds,"data", fillvalue = 0)[:]
# [missing, 11., 12., 13.] を返します。

# 時間単位を使用します: 2000-01-01 からの日数
@show cfvariable(ds,"data", units = "days since 2000-01-01")[:]
# [DateTime(2000,1,11), DateTime(2000,1,12), DateTime(2000,1,13), DateTime(2000,1,14)] を返します。

close(ds)
```
