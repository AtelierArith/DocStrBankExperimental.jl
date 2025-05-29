```
metadata_pkg(T; args...)
```

モデル `T` を提供するパッケージのメタデータを書くためのヘルパー関数です。ブロードキャスティングを使用して、一連のモデルを提供するパッケージのメタデータを定義します。

## キーワード

  * `package_name="unknown"`   : パッケージ名
  * `package_uuid="unknown"`   : パッケージUUID
  * `package_url="unknown"`    : パッケージURL
  * `is_pure_julia=missing`    : パッケージが純粋なJuliaかどうか
  * `package_license="unknown"`: パッケージライセンス
  * `is_wrapper=false` : パッケージがラッパーかどうか

## 例

```julia
metadata_pkg.((KNNRegressor, KNNClassifier),
    package_name="NearestNeighbors",
    package_uuid="b8a86587-4115-5ab1-83bc-aa920d37bbce",
    package_url="https://github.com/KristofferC/NearestNeighbors.jl",
    is_pure_julia=true,
    package_license="MIT",
    is_wrapper=false)
```
