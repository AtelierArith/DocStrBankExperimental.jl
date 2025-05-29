jpp =      + f[i-1, j  ] * h[i,   j-1]     - f[i-1, j  ] * h[i,   j+1]     - f[i,   j-1] * h[i-1, j  ]     + f[i,   j-1] * h[i+1, j  ]     + f[i,   j+1] * h[i-1, j  ]     - f[i,   j+1] * h[i+1, j  ]     - f[i+1, j  ] * h[i,   j-1]     + f[i+1, j  ] * h[i,   j+1]

jpc =     + f[i-1, j  ] * h[i-1, j-1]     - f[i-1, j  ] * h[i-1, j+1]     - f[i,   j-1] * h[i-1, j-1]     + f[i,   j-1] * h[i+1, j-1]     + f[i,   j+1] * h[i-1, j+1]     - f[i,   j+1] * h[i+1, j+1]     - f[i+1, j  ] * h[i+1, j-1]     + f[i+1, j  ] * h[i+1, j+1]

jcp =      - f[i-1, j-1] * h[i-1, j  ]     + f[i-1, j-1] * h[i,   j-1]     + f[i-1, j+1] * h[i-1, j  ]     - f[i-1, j+1] * h[i,   j+1]     - f[i+1, j-1] * h[i,   j-1]     + f[i+1, j-1] * h[i+1, j  ]     + f[i+1, j+1] * h[i,   j+1]     - f[i+1, j+1] * h[i+1, j  ]

return (jpp + jpc + jcp) * inv(hx) * inv(hv) / 12
