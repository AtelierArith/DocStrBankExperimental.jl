```
combinedef(dict::Dict)
```

`combinedef`は[`splitdef`](@ref)の逆です。これは`splitdef`のようなDictを受け取り、関数定義を返します。

この関数はおおよそ以下のことを行います（ただし、元の関数定義に実際に現れなかった部分を出力しないように、より洗練されています）。

```julia
rtype = get(dict, :rtype, :Any)
all_params = [get(dict, :params, [])..., get(dict, :whereparams, [])...]
:(function $(dict[:name]){$(all_params...)}($(dict[:args]...);
                                            $(dict[:kwargs]...))::$rtype
      $(dict[:body])
  end)
```
