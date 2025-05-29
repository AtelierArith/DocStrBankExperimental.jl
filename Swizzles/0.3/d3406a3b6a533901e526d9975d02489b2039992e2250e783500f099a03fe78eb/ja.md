```
@swizzle v.xyz
@swizzle v.rgb
@swizzle T v.xyz
@swizzle v[].some.expression().xyz
@swizzle v.xyz = [1, 2, 3]
@swizzle v.rgb = @swizzle v.bgr
@swizzle begin
  a.yz = b.xz
  b.w = a.x
end
```

スワイジング操作を実行し、コンポーネントを抽出するか、代入が提供されている場合はそれらを変更します。

このマクロは、提供された式内の `x.<field1><field2>...<fieldn>` フィールドアクセス構文（例：`x.xwyz`）を、[`swizzle`](@ref)（非変更）または [`swizzle!`](@ref)（変更）への適切な呼び出しに変換します。

追加の型引数 `T` を提供することで、非変更のスワイジング抽出の結果を特定の型に入れることができます（詳細については [`swizzle`](@ref) のドキュメントを参照してください）。これは、変更スワイジングには影響しません。

右辺の `.` の各文字は別々のコンポーネント名と見なされ、デフォルトでは次のようにマッピングされます：

  * `x` または `r` -> 最初のコンポーネント
  * `y` または `g` -> 2 番目のコンポーネント
  * `z` または `b` -> 3 番目のコンポーネント
  * `w` または `a` -> 4 番目のコンポーネント

これは、幾何処理（`[x, y, z, w]` が空間座標を表す）およびコンピュータグラフィックス（`[r, g, b, a]` が色ベクトルを表す）からの命名法を使用しています。

このマッピングは、Julia 1.11 以降にカスタマイズ可能です（拡張ヘルプを参照）。

# 拡張ヘルプ

Julia 1.11 以降、[スコープ付き値](https://docs.julialang.org/en/v1.11-dev/base/scopedvalues/)を使用すると、`@with Swizzles.component_names => Dict(...)` を介してこのコンポーネントマッピングをカスタマイズできます。たとえば、幅、高さ、深さを最初、2 番目、3 番目のコンポーネントと見なしたい場合は、次のようにします。

```julia
new_names = Dict('w' => 1, 'h' => 2, 'd' => 3)

# 既存の名前を破棄するために `@with Swizzles.component_names[] => new_names` を使用することもできます。
@with Swizzles.component_names => merge(Swizzles.component_names[], new_names) begin
  # 注意：ここでの `@eval` は重要です。
  # これは、スコープ付き値が設定される前に `@swizzle` が実行されるのを防ぎます。
  @eval begin
    @swizzle [10, 20, 30].w
    @swizzle [10, 20, 30].whd
  end
  # `include` されたファイル内の `@swizzle` マクロ呼び出しも影響を受けます。
  include("file.jl")
end
```

便利なことに、このパッケージによってエクスポートされたものを影にする独自の `@swizzle` マクロを定義することもできます。

```julia
using Swizzles

macro _swizzle(ex)
  new_names = Dict('w' => 1, 'h' => 2, 'd' => 3)
  swizzle_ex = @with Swizzles.component_names => merge(Swizzles.component_names[], new_names) begin
    # 第二引数として `T` パラメータを渡すこともできます。
    Swizzles.generate_swizzle_expr(ex)
  end
  esc(swizzle_ex)
end

@_swizzle [10, 20, 30].hd
```

これが良いアイデアかどうかは、あなたが決めることです。
