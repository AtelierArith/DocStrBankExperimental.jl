```
FV = loft(C1, C2; n_steps::Int=0, closed=true, type=:quad) -> GMTfv
```

2つの入力3D曲線の間に表面メッシュを（線形に）ロフトします。

### 引数

  * `C1, C2`: 3D曲線を*ロフト*するために定義された2つのMx3の点の行列。各行は3D空間の点です。

### キーワード引数

  * `n_steps`: ロフトされた表面を構築するために使用されるステップの数。`0`（デフォルト）の場合、ステップの数は曲線の点間隔から計算されます。
  * `closed`: `true`（デフォルト）の場合、`C1`と`C2`で作成された平面で上部と下部でロフトされた表面を閉じます。
  * `type`: ロフトされた表面を構築するために使用される面のタイプ（`:quad`（デフォルト）、`:tri`）。

### 例

```julia
ns=75; t=linspace(0,2*pi,ns); r=5; x=r*cos.(t); y=r*sin.(t); z=zeros(size(x));
C1=[x[:] y[:] z[:]];

f(t) = r + 2.0.* sin(6.0*t)
C2 = [(f(t)*cos(t),f(t)*sin(t),3) for t in range(0, 2pi, ns)];
C2 = stack(C2)'

FV = loft(C1, C2);
viz(FV, pen=0)
```
