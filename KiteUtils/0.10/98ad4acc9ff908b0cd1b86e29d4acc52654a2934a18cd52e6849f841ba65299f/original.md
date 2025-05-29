```
rot(pos_kite, pos_before, v_app)
```

Calculate the rotation matrix of the kite based on the position of the last two tether particles and the apparent wind speed vector. Assumption:  The kite aligns with the apparent wind direction. If used for the model `KPS4`, pass the vector `-x` of the kite reference frame instead of v_app. 
