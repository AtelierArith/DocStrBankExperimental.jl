```
transportoperator(grd, w)
```

与えられた沈降速度 `w` のための transportoperator を返します。

沈降速度はスカラー（例：`w = 100.0` メートル毎秒の単位）または深さの関数（例：`w(z) = 2z + 1`）として提供できます。

# 例

沈降速度 100m/s の粒子フラックスの発散を作成します。

```julia-repl
julia> T = transportoperator(grd, 100.0)
```

または沈降速度関数 w(z) = 2z + 1 を使用します。

```julia-repl
julia> T = transportoperator(grd, z -> 2z + 1)
```

デフォルトでは、海底フラックスはゼロに設定されているため、海底に到達したすべての粒子はそこで再鉱化されます。`fsedremin=0.0` を設定することで粒子が通過できるようにすることができます。例えば、

```julia-repl
julia> T = transportoperator(grd, z -> 2z + 1; fsedremin=0.0)
```

より細かい制御や高度な使用については、粒子フラックスの発散演算子関数 `PFDO` を参照してください。
