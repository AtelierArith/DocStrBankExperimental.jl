```julia
struct Joint{T, JT<:RigidBodyDynamics.JointType{T}}
```

ジョイントは、2つの剛体間の相対ツイストの運動学的制約を次元 $k$ の線形部分空間に制限します。

ジョイントには方向があります。ジョイントの前にある剛体はジョイントの前駆体と呼ばれ、ジョイントの後にある剛体はその後継体と呼ばれます。

ジョイントに関連する状態は、次の2つの変数のセットによってパラメータ化されます。

  * 相対的な同次変換をパラメータ化するベクトル $q \in \mathcal{Q}$。
  * 相対的なツイストをパラメータ化するベクトル $v \in \mathbb{R}^k$。

後継体のツイストは前駆体に対して $v$ の線形関数です。

いくつかのジョイントタイプ（特に、単位クォータニオンのような相対的な向きの冗長な表現を使用するもの）では、$q$ の時間微分である $\dot{q}$ は $v$ と同じではない場合があります。しかし、$\dot{q}$ と $v$ の間には可逆な線形変換が存在します。

参照：

  * Duindamの「Port-Based Modeling and Control for Efficient Bipedal Walking Robots」の定義2.9、2006年。
  * Featherstoneの「Rigid Body Dynamics Algorithms」の第4.4節、2008年。
