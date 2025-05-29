```
mjr_blitBuffer(src, dst, flg_color, flg_depth, con)
```

Blit from src viewpoint in current framebuffer to dst viewport in other framebuffer. If src, dst have different size and flg*depth==0, color is interpolated with GL*LINEAR.
