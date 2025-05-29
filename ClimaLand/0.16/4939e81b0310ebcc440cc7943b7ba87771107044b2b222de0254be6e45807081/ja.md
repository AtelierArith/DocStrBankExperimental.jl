```
LandSoilBiogeochemistry{FT}(;
    soil_args::NamedTuple = (;),
    biogeochemistry_args::NamedTuple = (;),
) where {FT}
```

`LandSoilBiogeochemistry`モデルのコンストラクタで、各コンポーネントに必要な引数を受け取り、それらのモデルを構築し、それらから`LandSoilBiogeochemistry`を構築します。

各コンポーネントモデルは、境界条件、ソース項、および相互作用項を含む、時間を進めるために必要なすべてのものを持って構築されます。

パラメータや駆動大気データなどの追加の引数は、必要に応じて渡すことができます。
