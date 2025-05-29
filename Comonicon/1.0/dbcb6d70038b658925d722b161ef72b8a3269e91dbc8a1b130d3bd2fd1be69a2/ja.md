```
@cast <function definition>
@cast <module definition>
```

Juliaの式はコマンドを示します。式が関数定義であれば、リーフコマンドとして解析され、式がモジュール定義またはモジュール名であれば、ノードコマンドとして解析されます。このマクロは、マルチコマンドCLIを作成するために[`@main`](@ref)と一緒に使用する必要があります。

# クイック例

```julia
# スクリプトまたはモジュール内

"""
2つの数を合計します。

# 引数

- `x`: 最初の数
- `y`: 2番目の数

# オプション

- `-p, --precision=<type>`: 計算の精度。

# フラグ

- `-f, --fastmath`: fastmathを有効にします。

"""
@cast function sum(x, y; precision::String="float32", fastmath::Bool=false)
    # 実装
    return
end

"2つの数の積"
@cast function prod(x, y)
    return
end

@main
```
