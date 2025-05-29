```
@newmodel name parent paramstype [sitemodel = true]
```

これは上記とまったく同じですが、非GCモデル用です。この構造体にはすべてのグループパラメータがありません。サイトはグループではなく、メインコンポーネントに関連付けられており、それぞれのフィールド名はそれに応じて名付けられています。

このモデルでサイトを使用するかどうかを示すオプションのboolを渡すことができます。デフォルトは`true`です。

## 例

```julia
struct MySAFTParam
    a::SingleParam{Float64}
    b::SingleParam{Float64}
    epsilon_assoc::AssocParam{Float64}
    bondvol::AssocParam{Float64}
end

@newmodel MySAFT SAFTModel MySAFTParam #サイトを持つモデルを定義します

struct MyModelParam
    a::SingleParam{Float64}
    b::SingleParam{Float64}
end

@newmodel MyModel EoSModel MyModelParam false #サイトなしのモデルを定義します
```
