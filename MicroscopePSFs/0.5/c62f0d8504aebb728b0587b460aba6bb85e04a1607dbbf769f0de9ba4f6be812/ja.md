```
GaussianPSF(psf::AiryPSF)
```

AiryPSFをFWHMを一致させることによって近似的なGaussianPSFに変換します。

σ ≈ 0.22 * λ/NAという関係を使用します。
