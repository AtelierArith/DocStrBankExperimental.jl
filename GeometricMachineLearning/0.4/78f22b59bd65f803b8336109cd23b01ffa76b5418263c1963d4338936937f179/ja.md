```
SymplecticAutoencoder(full_dim, reduced_dim)
```

`full_dim` と `reduced_dim` の次元の `SymplecticAutoencoder` のインスタンスを作成します。

# アーキテクチャ

シンプレクティックオートエンコーダのアーキテクチャは [brantner2023symplectic](@cite) で紹介されました。他のオートエンコーダと同様に、*エンコーダ* $\Psi^e:\mathbb{R}^{2N}\to\mathbb{R}^{2n}$ と *デコーダ* $\Psi^d:\mathbb{R}^{2n}\to\mathbb{R}^{2N}$ から構成され、$n\ll{}N$ です。これらは以下の特性を満たします：

$$
\begin{aligned}
    \nabla_z\Psi^e\mathbb{J}_{2N}(\nabla_z\Psi^e\mathbb{J}_{2N})^T = \mathbb{J}_{2n} & \quad\text{および} \\
    (\nabla_\xi\Psi^d)^T\mathbb{J}_{2N}\nabla_\xi\Psi^d = \mathbb{J}_{2n}. & 
\end{aligned}
$$

デコーダがこの特定の特性を持っているため、縮小されたシステムはハミルトニアン $H\circ\Psi^d$ によって記述できます：

$$
\mathbb{J}_{2n}\nabla_\xi(H\circ\Psi^d) = \mathbb{J}_{2n}(\nabla_\xi\Psi^d)^T\nabla_{\Psi^d(\xi)}H = \mathbb{J}_{2n}(\nabla_\xi\Psi^d)^T\mathbb{J}_{2N}^T\mathbb{J}_{2N}\nabla_{\Psi^d(\xi)}H = (\nabla_\xi\Psi^d)^+X_H(\Psi^d(\xi)),
$$

ここで $(\nabla_\xi\Psi^d)^+$ は $\nabla_\xi\Psi^d$ の *シンプレクティック逆* です（詳細については [`AutoEncoder`](@ref) 型のドキュメントを参照してください）。

# 引数

必須の引数 `full_dim` と `reduced_dim` に加えて、以下のキーワード引数を提供できます：

  * `n_encoder_layers::Integer = 4`: 1つのエンコーダブロックの層の数。
  * `n_encoder_blocks::Integer = 2`: エンコーダブロックの数。
  * `n_decoder_layers::Integer = 1`: 1つのデコーダブロックの層の数。
  * `n_decoder_blocks::Integer = 3`: デコーダブロックの数。
  * `sympnet_upscale::Integer = 5`: GSympNet の *アップスケーリング次元*。[`GradientLayerQ`](@ref) と [`GradientLayerP`](@ref) を参照してください。
  * `activation = tanh`: 勾配層での活性化。
  * `encoder_init_q::Bool = true`: 各エンコーダブロックの最初の層が $q$ 型であるべきかどうかを指定します。
  * `decoder_init_q::Bool = true`: 各デコーダブロックの最初の層が $p$ 型であるべきかどうかを指定します。
