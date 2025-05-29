```julia
attach!(
    mechanism,
    parentbody,
    childmechanism;
    child_root_pose,
    bodymap,
    jointmap
)

```

`childmechanism`のコピーを`mechanism`に接続します。

基本的には、`childmechanism`のコピーのルートボディを`mechanism`に属する`parentbody`で置き換えます。

注意: `childmechanism`の重力加速度は無視されます。

キーワード引数:

  * `child_root_pose`: `parentbody`に対する`childmechanism`のルートボディのデフォルトフレームのポーズ。デフォルト: 単位変換。
  * `bodymap::AbstractDict{RigidBody{T}, RigidBody{T}}`: 入力メカニズムのボディから出力メカニズムのボディへのマッピングで埋められます
  * `jointmap::AbstractDict{<:Joint{T}, <:Joint{T}}`: 入力メカニズムのジョイントから出力メカニズムのジョイントへのマッピングで埋められます

ここで、`T`は`mechanism`の要素タイプです。
