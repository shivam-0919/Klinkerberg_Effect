# Klinkerberg_Effect

### Project Overview
This project demonstrates the prediction of liquid permeability (absolute permeability) from gas permeability measurements using the Klinkenberg effect. 
It employs the Newton-Raphson iterative method to solve the non-linear equation derived from the Klinkenberg correlation.

### Background: The Klinkenberg Effect
The Klinkenberg effect describes the phenomenon where gas permeability measured in porous media is higher than the liquid permeability due to 'gas slippage' at the pore walls. 
The relationship is typically given by:

1.  `k(g) = k(l) + c(1/pm)`
   
where:
*   `kg` = measured gas permeability
*   `pm` = mean pressure
*   `kL` = equivalent liquid permeability (absolute permeability)
*   `c` = slope of the line
The constant c is related to kL by an empirical correlation: 
3. `c = b * k(l) = 6.9 * kL^(-0.36)`

Substituting c into the first equation and rearranging to solve for kL gives a non-linear equation:
3. `6.9 * kL^(0.64) + pm * kL - pm * kg = 0`

### Procedure: Newton-Raphson Iterative Method
Equation 3 is non-linear and can be solved iteratively using the Newton-Raphson method. The iterative formula is:

`k(i+1) = k(i) - (f(ki) / f'(ki))`

where:
*   `ki` = initial guess of the absolute permeability, md
*   `ki+1` = new permeability value for the next iteration
*   `i` = iteration level
*   `f(ki)` = Equation 3
*   `f'(ki)` = first-derivative of Equation 3

4.  The first derivative of Equation 3 with respect to `kL` is:
    `f'(ki) = 4.416 * ki^(-0.36) + pm`
The iterative procedure continues until convergence is achieved, meaning `f(ki)` approaches zero or successive `ki` values show negligible change.

### Example
A core plug's permeability is measured by air. Only one measurement is made at a mean pressure of 2.152 psi. 
The air permeability is 46.6 md. Estimate the absolute permeability of the core sample and compare it with the actual absolute permeability of 23.66 md.

### How to Run the Code:
1.  **Input Parameters:** The code will prompt you to enter the following values:
    *   `Enter your first guess of absolute permeability kl:` (e.g., `50`)
    *   `Enter Mean Pr. Pm:` (e.g., `2.152`)
    *   `Enter K(air) = kg:` (e.g., `46.6`)
2.  **Execution:** The script will then run the Newton-Raphson iteration and print the calculated absolute permeability.

## Expected Output (for the given example):

```
Enter your first guess of absolute permeability kl: 50
Enter Mean Pr. Pm: 2.152
Enter K(air) = kg: 46.6
The final value of Perm K is : 22.84900220489256
```

This calculated value (approximately 22.85 md) is close to the actual absolute permeability of 23.66 md, demonstrating the effectiveness of the method.

### Reference:

(Courtesy- Tarek Ahmed)


