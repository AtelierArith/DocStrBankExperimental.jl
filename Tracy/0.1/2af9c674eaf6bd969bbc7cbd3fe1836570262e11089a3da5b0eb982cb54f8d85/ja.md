```
@tracepoint "name" color=<color> enabled=<expr> <expression>
```

トレースしたいコードは `@tracepoint` で囲む必要があります。

```julia
@tracepoint "name" <expression>
```

通常、式は `begin-end` ブロックになります：

```julia
@tracepoint "data aggregation" begin
    # ここで多くの計算を行います...
end
```

トレースポイントの名前はリテラル文字列でなければならず、実行時に変更することはできません。トレースポイントは、`enabled` キーワード引数を使用することで動的に無効化または有効化できます。この引数はブール式である必要があります。

ゾーンの（デフォルトの）色は、マクロの `color` キーワード引数で設定でき、リテラルである必要があります。リテラルは次のいずれかです：

  * 整数：色の16進コード `0xRRGGBB`。
  * シンボル：`：black`、`：blue`、`：green`、`：cyan`、`：red`、`：magenta`、`：yellow`、`：white`、`：light_black`、`：light_blue`、`：light_green`、`：light_cyan`、`：light_red`、`：light_magenta`、`：light_yellow`、`：light_white` のいずれかの値を取ることができます。
  * 3つの整数のタプル：RGB値 `(R, G, B)` で、各値は 0..255 の範囲内である必要があります。

関数定義をトレースすることもでき、トレースポイントの名前は関数の名前になりますが、明示的に提供されている場合はその限りではありません：

```julia
@tracepoint function f(x)
    x^2
end

@tracepoint "calling g" g(x) = x^2

h = @tracepoint x -> x^2
```

Tracyがインストールされていない場合は、`TracyProfiler_jll` をインストールし、`run(TracyProfiler_jll.tracy(); wait=false)` で開始できます。

```jldoctest
julia> x = rand(10,10);

julia> @tracepoint "multiply" x * x;

julia> @tracepoint "pow2" color=:green x^2; # green

julia> @tracepoint "pow3" color=:0xFF0000 x^3; # red

julia> @tracepoint "pow4" color=(255, 165, 0) x^4; # orange

julia> timings_enabled() = rand() < 0.5;

julia> @tracepoint "pow5" enabled=timings_enabled() x^5; # timings_enabled() が true の場合のみ有効
```

Tracyがインストールされていない場合は、`TracyProfiler_jll` をインストールし、`run(TracyProfiler_jll.tracy(); wait=false)` で開始できます。
