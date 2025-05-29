```
v = cfvariable(ds::NCDataset,varname::SymbolOrString; <attrib> = <value>)
```

データセット `ds` から変数 `varname` を `NCDataset.CFVariable` として返します。キーワード引数 `<attrib>` は CF 規約に関連する属性（`fillvalue`、`missing_value`、`scale_factor`、`add_offset`、`units`、および `calendar`）です。これらの属性の値を指定することで、データセットに指定された値を上書きできます。属性が `nothing` に設定されている場合、その属性は読み込まれず、対応する変換は無視されます。この関数は、いくつかの変数属性を上書きできる追加の柔軟性を持つ `ds[varname]` に似ています。

例:

```julia
NCDataset("foo.nc","c") do ds
  defVar(ds,"data",[10., 11., 12., 13.], ("time",), attrib = Dict(
      "add_offset" => 10.,
      "scale_factor" => 0.2))
end

# 保存された（パックされた）値は [0., 5., 10., 15.]
# これは 0.2 .* [0., 5., 10., 15.] .+ 10 の結果です [10., 11., 12., 13.]

ds = NCDataset("foo.nc");

@show ds["data"].var[:]
# returns [0., 5., 10., 15.]

@show cfvariable(ds,"data")[:]
# returns [10., 11., 12., 13.]

# add_offset も scale_factor も適用されていない
@show cfvariable(ds,"data", add_offset = nothing, scale_factor = nothing)[:]
# returns [0, 5, 10, 15]

# add_offset は適用されるが scale_factor は適用されない
@show cfvariable(ds,"data", scale_factor = nothing)[:]
# returns [10, 15, 20, 25]

# 0 がフィル値として宣言される（add_offset と scale_factor は通常通り適用される）
@show cfvariable(ds,"data", fillvalue = 0)[:]
# return [missing, 11., 12., 13.]

# 時間単位を使用: 2000-01-01 からの日数
@show cfvariable(ds,"data", units = "days since 2000-01-01")[:]
# returns [DateTime(2000,1,11), DateTime(2000,1,12), DateTime(2000,1,13), DateTime(2000,1,14)]

close(ds)
```
