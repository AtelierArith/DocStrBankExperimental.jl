```
@setpkg command[ command-arguments... ]
```

@setpkg マクロは、開発者とユーザーの間でセットを共有することを可能にします。

# コマンド

## load: ローカルファイルからセットを読み込みます。これはセットファイルとも呼ばれます。

```
@setpkg load <path/to/file>
```

セットファイルは、SetBuilders 用にカスタマイズされた通常の Julia モジュールです。

# 例

ファイル `myset.sjl` に次の Julia コードが含まれていると仮定します。

```julia
module MySetModule

export MYSET

I = @setbuild(Integer)
MYSET = @setbuild(x in I, x > 0)

end
```

`MYSET` は以下の例のように使用できます。

```julia-repl
julia> @setpkg load "myset.sjl"

julia> using SetBuilders.MySetModule

julia> 1 in MYSET
true

julia> 0 in MYSET
false
```

!!! note
    "sb_" で始まるキーワード名は、SetBuilders の内部使用のために予約されています。

