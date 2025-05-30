```
RBDFAST(; num_harmonics = 6)
```

  * `num_harmonics`: パワースペクトル密度分析中に考慮する調和数。

## メソッドの詳細

ランダムバランスデザイン（RBD）メソッドでは、`eFAST`と同様に、入力空間の曲線上に`samples`ポイントが選択されます。各因子に対して固定周波数`1`が使用されます。次に、設計ポイントを生成するために、サンプルポイントの座標に独立したランダムな置換が適用されます。分析のための入力モデルは各設計ポイントで評価され、出力は因子`Xi`に関して増加順に設計ポイントが並ぶように再配置されます。フーリエスペクトルは、周波数1およびその高調波（2、3、4、5、6）でモデル出力に対して計算され、因子`Xi`の感度指数の推定値が得られます。

## API

```
gsa(f, method::RBDFAST; num_params, samples,
         rng::AbstractRNG = Random.default_rng(), batch = false, kwargs...)
```

### 例

```julia
function linear_batch(X)
    A= 7
    B= 0.1
    @. A*X[1,:]+B*X[2,:]
end
function linear(X)
    A= 7
    B= 0.1
    A*X[1]+B*X[2]
end

lb = -ones(4)*π
ub = ones(4)*π

rng = StableRNG(123)
res1 = gsa(linear,GlobalSensitivity.RBDFAST(),num_params = 4, samples=15000)
res2 = gsa(linear_batch,GlobalSensitivity.RBDFAST(),num_params = 4, batch=true, samples=15000)
```
