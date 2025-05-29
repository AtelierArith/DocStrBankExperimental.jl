`HMatrix`はSMatrix{4,4}をラップし、以下を強制します。

  * サイズ4x4が定義されている
  * 回転行列[1:3,1:3]の単位列
  * 最後の行は0001
  * `data::StaticArraysCore.MMatrix`
