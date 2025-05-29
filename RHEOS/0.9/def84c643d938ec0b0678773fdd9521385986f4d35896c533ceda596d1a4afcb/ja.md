```
RheoModelClass(;name::String, p::Tuple, G,J,Gp,Gpp, constraint, info, G_ramp)
```

`RheoModelClass`は、RHEOSがモデルをフィットさせ、パラメータが設定された後に予測を行うために必要なすべての関連データを含む複雑なデータ構造です。RHEOSは、MaxwellやKelvinVoigtなどの一般的なレオロジーモデルを表現するためのこのようなデータ構造をすでに多数持っています。

ユーザーはRheoModelClassオブジェクトの内容を直接操作することは期待されていませんが、フィッティングや粘弾性モジュラスの数値評価のために関連する関数に渡すことになります。

モデル名とそのパラメータは、REPLに印刷して表示することができます。

# 例

```@example
julia> Maxwell

Model name: maxwell

Free parameters: η and k

                ___
            _____| |________╱╲  ╱╲  ╱╲  ___
                _|_|          ╲╱  ╲╱  ╲╱
                  η                  k
               
```
