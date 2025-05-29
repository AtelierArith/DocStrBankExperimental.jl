`t,y,z,x = solve(dmp, t = 0:length(dmp.t)-1; y0 = _1(dmp), g = dmp.g, solver=ode45)`

`t` 時間ベクトル

## キーワード引数:

`y0` 開始位置、デフォルトは `dmp` のトレーニングデータの初期点 `g` 目標、デフォルトは `dmp` の目標

`solver` 使用するODEソルバー、詳細は https://github.com/JuliaLang/ODE.jl を参照

デフォルトのソルバーは `solver=ode54` で、より高速な代替は `solver=euler` です

`plotdmp` も参照してください
