```
getdetJdV_average(cv::InterfaceCellValues, qp::Int)
```

Return the average of the product between the determinant of the Jacobian on each side of the interface and the quadrature point weight for the given quadrature point: $\det(J(\mathbf{x})) w_q$.

This value is typically used when integrating a function on the mid-plane of an interface element.
