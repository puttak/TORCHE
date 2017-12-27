# TORCHE
This is a collection of Python scripts for pressure drop and heat transfer calculations for crossflow tube bundles for both inline and staggered configurations.

Author: Jonah Haefner* and Lane Carasik^
Contributing and previous work done by: Julien Clayton

*Texas A&M University
*Thermal-hydraulics Research Group

^Kairos Power LLC.
^Modeling and Simulation Group

These models are simple to use pressure drop and Nusselt Number calculators based off the work of Zukauskas et al. and Gnielinski and Gaddis. 
It is intended that future versions will include additional crossflow models in tube bundles, across helical coils, and across packed bends. 

## Pressure Drop

There is currently only two crossflow pressure drop models implemented. These are models developed by Zukauskas-Ulinskas and Gnielinski-Gaddis where the former is based off curve fits from old figures while the latter is a generalized set of equations based on inline or staggered geometries.

### Zukauskas Model

Validity:
- Will work for values of b = 1.25, 1.5, or 2
- Reynolds number needs to be below 150000

References:
1. A. ZUKAUSKAS, R. ULINSKAS, Heat Transfer in Banks of Tubes in Crossflow, Hemisphere Publishing, United States (1988).

This model implementation is discussed in detail in the following conference proceedings:

1. J. B. Haefner, L. B. Carasik, Y. A. Hassan, Development and Verification of MATLAB Functions for Pressure Drop Estimation in Crossflow Tube Bundles. In Transactions of the American Nuclear Society (Vol. 115(1), pp. 1535-1537). Las Vegas, Nevada

### Gnielinski & Gaddis Model

Notes:
- Not limited to specific pitch-diameter ratios
- Calculates the velcoity through the narrowest area
Validity:
* The available experimental measurements used to develop the above equations covered the following ranges: Reynolds number: 1 ≤ Re ≤ 3 /* 10E5 and number of tube rows: nR ≥  5.
* The tube bundles used in the experimental investigations had transverse and longitudinal pitch ratios as follows: 
 * In the range Re < 10E3: For in-line tube arrangement: a x b = 1:25 x 1:25; 1:5 x 1:5; 2:0 x 2:0. For staggered tube arrangement: a x b = 1:25 x 1:0825; 1:5 x 1:299; 1:768 x 0:884.
 * In the range Re ≥ 10E3: For in-line tube arrangement: 1:25 ≤ a ≤ 3:0; 1:2 ≤  b ≤  3:0. For staggered tube arrangement: 1:25 ≤  a ≤  3:0; 0:6 ≤  b ≤  3:0; c ≥ 1:25.

References:
1. VDI. VDI Heat Atlas. Berlin, Heidelberg: VDI-Buch-Springer, 2010. Chapter L1
2. Gaddis, E., Gnielinski, V., 1985, "Pressure drop in cross flow across tube bundles," Int. Chem. Eng., vol. 25(1), pp. 1-15

This 

## Heat Transfer

### Zukauskas Model
Zukauskas Model
        Cite: Zhukauskas, A., R. Ulinskas. Heat Transfer in Tube Banks in Crossflow.
        Hemisphere Publishing Corporation. New York, NY. 1988.
        
            Inputs:
            -Rho = density [kg/m^3]
            -u = free stream velocity without tubes [m/s]
            -a = transverse pitch ratio
            -b = longitudinal pitch ratio
            -a and b [m]
            -Reynolds number calculated based on velcoity at narrowest point
            - N = # of tubes
            - Pr = Prandtl Number
            - d = Tube Diameter
            - PrS = Wall Prandtl Number
            - v = kinematic viscosity (m^2/s)
            
            NOTE: Currently only applicable for staggered geometry
            Validity:10 < Re < 2e6
                     0.7 < Pr < 500
            Output:
              - Nusselt Number
### Gnielinski-Gaddis Model

Gnielinski and Martin Model
Based off Leveque Analogy
    Cite: Martin, H., 2002, “The Generalized Lévêque Equation and its practical use for the prediction of heat and mass transfer rates from pressure drop,” Chem. Eng. Sci., vol. 57, pp. 3217-3223.
    
        Inputs:
        -Rho [kg/m^3]
        -u = free stream velocity without tubes [m/s]
        - a = transverse pitch ratio
        - b = longitudinal pitch ratio
        - a and b [m]
        - Reynolds number calculated based on velcoity at narrowest point
        - N = # of tubes
        - geom = tube geometry (inline or staggered)
        - d= tube diameter
        - dh = hydraulic diameter
        - Pr = Prandtl Number
       
        Output:
        - Nusselt Number
