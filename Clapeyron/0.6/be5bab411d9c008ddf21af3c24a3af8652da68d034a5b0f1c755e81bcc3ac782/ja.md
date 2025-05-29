```
xy_flash(model,spec::FlashSpecifications,z,w0::FlashResult,method::GeneralizedXYFlash)
xy_flash(model,spec::FlashSpecifications,z,w0::FlashResult;rtol = 1e-12,atol = 1e-10,max_iters = 50)
```

任意の仕様で非反応性多相多成分フラッシュ問題を解決するルーチン。Ben Gharbia（2021）によって提案された統一された定式化に基づいています。必要な2つの仕様は`specs`から取得され、初期点は`w0`から得られます。モル分率、蒸気分率、モル体積、平衡温度および圧力を含む[`FlashResult`](@ref)構造体を返します。

## 例

```
spec = FlashSpecifications(p = 101325.0, T = 200.15) #p-Tフラッシュ
model = cPR(["ethane","propane"],idealmodel=ReidIdeal)
z = [0.5,0.5] #バルク組成
x1 = [0.25,0.75] #液体組成
x2 = [0.75,0.25] #気体組成
compositions = [x1,x2]
volumes = [6.44e-5,0.016]
fractions = [0.5,0.5]
p0,T0 = NaN,NaN #p-Tフラッシュでは、圧力と温度はすでに仕様です
data = FlashData(p0,T0)
result0 = FlashResult(compositions,fractions,volumes,data) #必要な情報をすべて含むFlashResult
result = xy_flash(model,spec,z,result) #フラッシュを実行
```
