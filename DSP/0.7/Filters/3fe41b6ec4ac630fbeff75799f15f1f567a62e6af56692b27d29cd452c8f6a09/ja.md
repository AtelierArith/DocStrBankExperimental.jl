```
remez(numtaps::Integer, 
      bands::Vector, 
      desired::Vector; 
      weight::Vector=[], 
      Hz::Real=1.0, 
      filter_type::RemezFilterType=filter_type_bandpass,
      maxiter::Integer=25, 
      grid_density::Integer=16)
```

これは3つの引数(numtaps、bands、desired)を必要とするscipy互換バージョンです。簡略化されたAPIについては、2つの引数バージョン(numtaps、band_defs)を参照してください。設計されたフィルタは同等であり、入力は異なる方法で指定されています。以下に、簡略化されたAPIバージョンと異なる引数と例が説明されています。

# 引数

  * `bands::Vector`: Hz単位のバンドエッジを含む単調増加のシーケンス。すべての要素は非負であり、`Hz`で指定されたサンプリング周波数の半分未満でなければなりません。
  * `desired::Vector`: 指定されたバンドごとの望ましいゲインを含む、bandsの半分のサイズのシーケンス。
  * `weight::Vector`: (オプション) 各バンド領域に与える相対的な重み付け。`weight`の長さは`bands`の長さの半分でなければなりません。
  * `filter_type::RemezFilterType`: デフォルトは`filter_type_bandpass`です。フィルタの種類：

      * `filter_type_bandpass` : バンド内でのフラットな応答。これがデフォルトです。
      * `filter_type_differentiator` : バンド内での周波数比例応答。`filter_type_hilbert`の場合の奇数対称ですが、線形傾斜の望ましい応答を持ちます。
      * `filter_type_hilbert` : 奇数対称のフィルタ、すなわち、タイプIII（偶数次数の場合）またはタイプIV（奇数次数の場合）の線形位相フィルタ。

# 例

簡略化されたAPIとScipy APIの例を比較します。以下の各ブロックは、まず簡略化された（推奨）APIを使用してフィルタを設計し、その後Scipy互換APIを使用して同じフィルタを設計します。

```jldoctest; setup = :(using DSP)
julia> bpass = remez(35, [(0, 0.1)=>0, (0.15, 0.4)=>1, (0.45, 0.5)=>0]);

julia> bpass = remez(35, [0, 0.1, 0.15, 0.4, 0.45, 0.5], [0, 1, 0]);

```

```jldoctest; setup = :(using DSP)
julia> bpass2 = remez(35, [(0, 0.08)=>0, (0.15, 0.4)=>1, (0.47, 0.5)=>0]);

julia> bpass2 = remez(35, [0, 0.08, 0.15, 0.4, 0.47, 0.5], [0, 1, 0]);

```

```jldoctest; setup = :(using DSP)
julia> h = remez(20, [(0.1, 0.95) => 1]; neg=true, Hz=2.0);

julia> h = remez(20, [0.1, 0.95], [1]; filter_type=filter_type_hilbert, Hz=2.0);

```

```jldoctest; setup = :(using DSP)
julia> h = remez(200, [(0.01, 0.99) => (f -> f/2, f -> 1/f)]; neg=true, Hz=2.0);

julia> h = remez(200, [0.01, 0.99], [1]; filter_type=filter_type_differentiator, Hz=2.0);

```
