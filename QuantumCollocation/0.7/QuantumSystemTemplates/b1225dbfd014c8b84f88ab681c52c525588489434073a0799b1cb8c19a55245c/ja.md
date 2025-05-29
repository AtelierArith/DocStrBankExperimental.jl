```
TransmonSystem(;
    ω::Float64=4.4153,  # GHz
    δ::Float64=0.17215, # GHz
    levels::Int=3,
    lab_frame::Bool=false,
    frame_ω::Float64=ω,
) -> QuantumSystem
```

トランスモンキュービットのための `QuantumSystem` オブジェクトを返し、ハミルトニアンは次のようになります。

$$
H = \omega a^\dagger a - \frac{\delta}{2} a^\dagger a^\dagger a a
$$

ここで `a` は消滅演算子です。

# キーワード引数

  * `ω`: トランスモンの周波数（GHz単位）。
  * `δ`: トランスモンの非調和性（GHz単位）。
  * `levels`: トランスモンのレベル数。
  * `lab_frame`: 実験室フレームのハミルトニアンを使用するか、ω回転フレームを使用するか。
  * `frame_ω`: 回転フレームの周波数（GHz単位）。
  * `mutiply_by_2π`: ハミルトニアンを2π倍するかどうか。周波数がGHz単位であるため、デフォルトでtrueに設定されています。
  * `lab_frame_type`: 使用する実験室フレームのハミルトニアンのタイプ。(:duffing, :quartic, :cosine)のいずれか。
  * `drives`: ハミルトニアンにドライブを含めるかどうか。
