```
xyf2loc(x, y, face) -> (z, phi, sintheta, have_sintheta)
```

Given a position encoded as XYF, return the tuple containing $z = cos(\theta)$, `\phi`, and optionally an accurate estimate for $sin(\theta)$ (if `have_sintheta` is `true`), where $\theta$ is the colatitude and $\phi$ is the longitude, both expressed in radians.
