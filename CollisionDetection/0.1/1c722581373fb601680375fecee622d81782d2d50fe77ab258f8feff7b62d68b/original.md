itsinbox(Opj*c, Obj*rad, box*c, box*hf, ratio) -> true/fasle

Finds out if the object with center position (Opj*c) and (Obj*rad) fits inside the box.   It uses the box dimension (box*c, and box*hf(w/2)) to do the comparsion   ratio is relative to box half width, so if you want to be just within the box   then ratio =1, if the boundaries of the object is slightly bigger and you still   want to include them make ratio bigger ex:1.2
