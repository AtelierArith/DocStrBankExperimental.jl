```
ply2surface(ply_dir, splash_dir, radius, num_threads; cube_size=0.6, 
    surface_threshold=0.6, smoothing_length=1.2, splashsurf="nothing")
```

## Description:

  * radius: particle (primitive) radius should be half of the particle's diameter.
  * smoothing-length: It should be set around 1.2. The larger the value, the smoother the isosurface, but it will also artificially increase the fluid volume.
  * surface-threshold: It can be used to offset the increase in fluid volume caused by factors such as larger particle radius, and a threshold of 0.6 seems to work quite well.
  * cube-size: Typically, it should not exceed 1. If the results are rough or the runtime is long, start increasing or decreasing from between 0.5 to 0.75.

---

  * 半径：粒子(原始)半径，应该是粒子直径的一半
  * 光滑长度：应围绕1.2设置。值越大，等值面越平滑，但也会人为地增加流体体积
  * 表面阈值：可以用来抵消由于较大粒子半径等因素导致的流体体积增加,0.6的阈值似乎效果不错
  * 立方体尺寸：通常不能大于1,如果结果粗糙或者运行时间长,从0.5~0.75之间开始增大或减小
