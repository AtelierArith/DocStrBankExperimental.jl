```
function boundary_average(patch::Symbol, field, config; time=0)
    # メッシュオブジェクトを抽出
    mesh = field.mesh

    # バウンダリーパッチのID（インデックス）を決定
    ID = boundary_index(mesh.boundaries, patch)
    @info "インデックス $ID でパッチ: $patch の平均を計算中"
    boundary = mesh.boundaries[ID]
    (; IDs_range) = boundary

    # ユーザーが提供したのと同じタイプのフェイスフィールドを作成（スカラーまたはベクトル）
    sum = nothing
    if typeof(field) <: VectorField 
        faceField = FaceVectorField(mesh)
        sum = zeros(_get_float(mesh), 3) # ゼロベクトルを作成
    else
        faceField = FaceScalarField(mesh)
        sum = zero(_get_float(mesh)) # ゼロを作成
    end

    # CFD結果をバウンダリに補間
    interpolate!(faceField, field, config)
    correct_boundaries!(faceField, field, field.BCs, time, config)

    # 平均を計算
    for fID ∈ IDs_range
        sum += faceField[fID]
    end
    ave = sum/length(IDs_range)

    # 平均を返す
    return ave
end
```
