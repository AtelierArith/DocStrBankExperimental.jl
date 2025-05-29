```
find_dstrain!(material::AbstractMaterial, dstrain::AbstractVector{<:Real},
              dt::Real, update_dstrain!::Function;
              max_iter::Integer=50, tol::Real=1e-9)
```

`material`のための適合するひずみ増分を見つけます。

新しい種類のひずみ最適化器を実装したい場合にのみ、この低レベルの関数を直接呼び出す必要があるでしょう。使用例については`general_increment!`および`stress_driven_general_increment!`を参照してください。

これは最適化器の骨組みです。個々の特定の最適化器関数（`update_dstrain!`）は、`dstrain`をどのように更新するかを定義するだけで済みます。骨組み自体はニュートン-ラフソンの根を見つけるものではありません。反復ループ、収束チェック、およびデータの配管を抽象化するだけで、他の種類のものの中でも、ニュートン-ラフソンの根を見つけるための便利な実装に使用できます。

この関数に供給される`dstrain`は、最適化の初期推測です。各反復で、ユーザー定義の補正器`update_dstrain!`によって更新されなければなりません。その呼び出しシグネチャは次のとおりです：

```
update_dstrain!(dstrain::V, dstress::V, jacobian::AbstractArray{T})
    where V <: AbstractVector{T} where T <: Real
  -> err::Real
```

`dstrain`は、Voigt形式のひずみ増分の現在の値です。テンソル形式への変換には`offdiagscale=2.0`を使用します。この関数は、Voigt形式の`dstrain`をインプレースで更新しなければなりません。

`dstress = stress - stress0`、ここで`stress`は、現在の`dstrain`の値を駆動ひずみ増分として使用して、材料を1タイムステップの長さ`dt`で統合することによって予測される応力状態であり、`stress0`は`materials.variables.stress`に保存されている応力状態です。

`jacobian`は∂σij/∂εkl（`material.variables_new.jacobian`）であり、材料実装によって計算されます。多くの場合、dstrainの最適化は実際にはニュートン-ラフソンの根を見つけることによって行うことができるため、更新式を書くのを容易にするためにjacobianを渡します。

戻り値`err`はエラー測定（Real, >= 0）でなければなりません。

更新は最大`max_iter`回反復され、`err`が`tol`を下回るまで続けられます。

`max_iter`に達し、エラー測定がまだ`tol`以上である場合、`ErrorException`がスローされます。

機能を直交させるために、タイムステップは**自動的に**コミットされません。`integrate_material!`を呼び出しますが、`update_material!`は呼び出しません。言い換えれば、`material.variables_new`のみを更新します。タイムステップをコミットするには、最適化器が完了した後に`update_material!`を呼び出してください。
