```
replacebond!(M::MPS, b::Int, phi::ITensor; kwargs...)
```

ITensor `phi`を因数分解し、MPS `M`のITensor `b`と`b+1`を因数で置き換えます。直交性は`ortho="left"/"right"`を選択します。
