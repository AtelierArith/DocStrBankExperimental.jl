```
RemotelySensedReflectance(rirr_in,wvbd_in,wvbd_out)
```

wvbd*inからwvbd*outでのリモートセンシング反射率を計算します。

```
wvbd_out=Float64.([412, 443, 490, 510, 555, 670])
wvbd_in=Float64.([400,425,450,475,500,525,550,575,600,625,650,675,700])
rirr_in=1e-3*[23.7641,26.5037,27.9743,30.4914,28.1356,
    21.9385,18.6545,13.5100,5.6338,3.9272,2.9621,2.1865,1.8015]

rrs_out=RemotelySensedReflectance(rirr_in,wvbd_in,wvbd_out)

using Plots
plot(vec(rrs_out),linewidth=4,lab="再計算されたRRS")
rrs_ref=1e-3*[4.4099, 4.8533, 5.1247, 4.5137, 3.0864, 0.4064]
plot!(rrs_ref,linewidth=4,ls=:dash,lab="参照結果")
```
