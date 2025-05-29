```
ESElectrolyte(solvents::Array{String,1}, 
    ions::Array{String,1}; 
    idealmodel::IdealModel = BasicIdeal,
    neutralmodel::EoSModel = pharmaPCSAFT,
    ionmodel::IonModel = DH,
    RSPmodel::RSPModel = ConstRSP,
    userlocations::Vector{String}=[],
    ideal_userlocations::Vector{String}=[],
    verbose::Bool=false)
```

## 説明

この関数は、理想、ニュートラル、およびイオンモデルを組み合わせて電解質モデルを作成するための必要なフレームワークを提供します：

```julia
model = ESElectrolyte(["water"],["sodium","chloride"];
            idealmodel = BasicIdeal,
            neutralmodel = pharmaPCSAFT,
            ionmodel = DH,
            RSPmodel = ConstRSP)  
```

Clapeyronで利用可能なモデルのいずれかを上記のように組み合わせることができます。ニュートラル（溶媒）種とイオンは別々に定義されることに注意してください。Clapeyron内では、イオンベースの電解質モデルのみをサポートします。そのため、塩が別の種として扱われる塩ベースのアプローチはサポートされません。
