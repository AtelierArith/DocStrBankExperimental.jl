dhtrans - Computes Denavit Hartenberg matrix

This function calculates the 4x4 homogeneous transformation matrix, representing the Denavit Hartenberg matrix of a robot arm link, given link parameters of joint angle, length, joint offset and twist.

```
Usage: T = dhtrans(theta, offset, length, twist)
 
Arguments:  theta - joint angle (rotation about local z)
           offset - offset (translation along z)
           length - translation along link x axis
            twist - rotation about link x axis

Returns:        T - 4x4 Homogeneous transformation matrix.
```

See also: trans(), rotx(), roty(), rotz(), invht()
