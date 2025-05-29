```
turbulent_fluxes!(dest,
                atmos::CoupledAtmosphere,
                model::AbstractModel,
                Y,
                p,
                t)
```

結合シミュレーションの地表での乱流表面フラックス項を計算します。この場合、カプラーはすでに乱流フラックスを計算し、各コンポーネントモデルで更新しているため、この関数は何もしません。
