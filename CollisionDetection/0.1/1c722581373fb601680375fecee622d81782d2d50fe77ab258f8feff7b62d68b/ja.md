itsinbox(Opj*c, Obj*rad, box*c, box*hf, ratio) -> true/fasle

オブジェクトの中心位置 (Opj*c) と (Obj*rad) がボックス内に収まるかどうかを判断します。ボックスの寸法 (box*c, および box*hf(w/2)) を使用して比較を行います。ratio はボックスの半幅に対する相対値であり、ボックス内に収まるようにしたい場合は ratio = 1 とします。オブジェクトの境界がわずかに大きく、まだそれを含めたい場合は、ratio を大きくします。例: 1.2
