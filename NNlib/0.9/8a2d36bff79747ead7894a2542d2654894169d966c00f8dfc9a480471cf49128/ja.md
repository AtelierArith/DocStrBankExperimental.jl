````
grid_sample(input::AbstractArray{T, 4}, grid::AbstractArray{T, 4}; padding_mode = :zeros)
grid_sample(input::AbstractArray{T, 5}, grid::AbstractArray{T, 4}; padding_mode = :zeros)

`input`を与えられたとき、`grid`からのピクセル位置で`input`の値をサンプリングして出力を計算します。出力値を計算するためにバイリニア補間を使用します。

この実装は、極値（`-1`と`1`）が入力のコーナーピクセルの中心点を指すものと見なされることを前提としています（すなわち、コーナーを揃えることが`true`です）。

# 引数

- `input`: `(W_in, H_in, [D_in,] C, N)`の形状の入力配列。
- `grid`: `(2, W_out, H_out, [D_out,] N)`の形状の入力グリッド。
    各`(W_out, H_out, [D_out,] N)`に対して、グリッドは`input`の形状で正規化されたサンプリング位置を指定する`(x, y [,z])`座標を含みます。

    したがって、`x`、`y`および[`z`]は`[-1, 1]`の範囲の値を持つ必要があります。
    例えば、`(x = -1, y = -1, [z = -1])`は`input`の左上[-前]ピクセルであり、
    `(x = 1, y = 1, [z = 1])`は`input`の右下後ろピクセルです。

    範囲外の値は`padding_mode`に従って処理されます。
- `padding_mode`: 範囲外のパディング。
    範囲外のグリッド位置に対して`0`を使用するには`:zeros`を指定します。
    範囲外のグリッド位置に対してボーダー値を使用するには`:border`を指定します。
    デフォルトは`:zeros`です。

# 戻り値

`input`からサンプリングされた`(W_out, H_out, [D_out,] C, N)`のグリッド。

# 例

以下の例では、グリッドには2つの範囲外サンプリング位置が含まれており、`padding_mode`に応じて異なる方法で処理されます。

```jldoctest
julia> x = reshape(collect(1.0:4.0), (2, 2, 1, 1))
2×2×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
1.0  3.0
2.0  4.0

julia> grid = Array{Float64}(undef, 2, 3, 2, 1);

julia> grid[:, 1, 1, 1] .= (-3, -1);

julia> grid[:, 2, 1, 1] .= (0, -1);

julia> grid[:, 3, 1, 1] .= (1, -1);

julia> grid[:, 1, 2, 1] .= (-1, 1);

julia> grid[:, 2, 2, 1] .= (0, 1);

julia> grid[:, 3, 2, 1] .= (3, 1);

julia> grid_sample(x, grid; padding_mode=:zeros)
3×2×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
0.0  3.0
1.5  3.5
2.0  0.0

julia> grid_sample(x, grid; padding_mode=:border)
3×2×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
1.0  3.0
1.5  3.5
2.0  4.0
```
````
