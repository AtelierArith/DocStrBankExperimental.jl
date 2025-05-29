```
sweep_contract(LTN::LabelledTensorNetwork, χ, τ;
    fast=false, valid=false, planar=false, connected=false, report=false)
sweep_contract(TN::TensorNetwork, χ, τ;
    fast=false, valid=false, planar=false, connected=false, report=false)
```

`TensorNetwork TN` または `LabelledTensorNetwork LTN` の収縮を返します。これは `arXiv:2101.04125` のスイープライン収縮アルゴリズムを使用しています。MPSは、任意のボンド次元が `τ` を超えるたびに、ボンド次元 `χ` に切り捨てられます。

デフォルトでは、ネットワークの有効性がチェックされ、平面化され、必要に応じてスイープ接続されます。キーワードフラグ `valid`、`planar`、および `connected` を使用してこれらをスキップすることができ、またフラグ `fast` を使用してすべてをスキップすることもできます。これらのフラグが有効になっている場合、収縮は不適切に形成されたネットワークで失敗する可能性があります。

アンダーフロー/オーバーフローの問題を避けるために、ネットワークの収縮値はタプル `(f::Float64, i::Int64)` として返されます。ここで `1≦f<2` または `f` は `0` であり、`f*2^i` の値を表します。関数 `ldexp` を使用してこれを Float64 に戻すことができます。

`sweep_contract` は非変異的であり、可能な限りネットワークのディープコピーに作用します。より効率的な変異的バージョン `sweep_contract!` を使用することをお勧めします。
