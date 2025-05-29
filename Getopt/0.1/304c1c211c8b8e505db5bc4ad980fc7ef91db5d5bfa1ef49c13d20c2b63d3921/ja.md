```
getopt(args::Array{String}, ostr::String, longopts::Array{String}=String[])
```

コマンドラインオプションをgetoptのようなインターフェースで反復処理し、`args`からオプションを削除します。

`args`は通常`ARGS`です。デフォルトでは、オプションは非オプション引数の後に出現することが許可されています。もし`ostr[1]=='+'`の場合、デフォルトの動作は無効になります。

# 例

```julia
for (opt, arg) in Getopt.getopt(ARGS, "xy:", ["foo", "bar="])
	@show (opt, arg)
end
@show ARGS # 非オプション引数のみが残ります
```
