# <h1 align="center">**`Proyecto Individual 2`**

<p align="center">
<img src="https://www.mapfreglobalrisks.com/media/Imagen-Portada-adaptada-1-2.jpg"   
>
</p>

## 🏥 **Estancia hospitalaria** 🏥

La estancia hospitalaria, cuando es prolongada constituye una preocupación mundial debido a sus efectos negativos en el sistema de salud, aumentando los costos, generando deficiencia en la accesibilidad de prestación de servicios de salud, saturación de unidades de hospitalización y urgencias, por consiguiente, mayores efectos adversos como lo son las enfermedades intrahospitalarias.
​
## **Descripción del problema**

Predecir si un paciente tendrá una estancia hospitalaria prolongada o no, para poder administrar la demanda de camas en el hospital según la condición de los pacientes recientemente ingresados. 

Para esto, se define que un paciente posee estancia hospitalaria prolongada si ha estado hospitalizado más de 8 días. 

## **Solucion propuesta**

Segun la interpretacion personal del presente proyecto, se propone resolver un problema del tipo clasificacion, es decir si se pertenece a una categoria o a otra. En este caso las categorias son estancia larga o estancia corta.

Se desarrollara uno de los modelos clásicos de clasificación: el de `árbol de decisión`, con una profundidad de 7 niveles ya que mas niveles no mejora el score del modelo.

Teniendo en cuenta lo anterior, a continuacion se muestra la matriz de confusion resultante del modelo aplicado, la cual es una herramienta que permite la visualización del desempeño de un algoritmo que se emplea en aprendizaje supervisado.

<p align="center">
<img src="_src\assets\Untitled.png"   
>
</p>

Ahora, podemos calcular algunas metricas que evaluaran al modelo desarrollado.

Comenzamos declarando 4 conceptos que se vinculan con los 4 cuadrantes de la matriz.

 # True Positive (TP)(1,1), es la cantidad de casos positivos (es decir en este problema se interepreta como la cantidad de casos en el que la estadia de un paciente es mayor a 8 dias) que el modelo pudo detectar correctamente.
 
 # False Negative (FN)(1,0), es la cantidad de casos negativos que el modelo detecto (es decir estadias cortas) pero su verdadera clasificacion es positiva, es decir estadia larga. 
 
 # False Positive (FP),(0,1) es la cantidad de casos que el modelo predijo como positivos (es decir con estadia mayor a 8 dias) pero su clasificacion es la contraria, es decir casos con estadias menores a 9 dias. 
 
 # True Negative (TN)(0,0), es la cantidad de casos negativos (es decir una estadia menor a 9 dias) que se predijeron correctamente.  

TP = mconf[1][1] = 61475
TN = mconf[0][0] = 4784 
FP = mconf[0][1] = 2211 (conocido como error tipo I)
FN = mconf[1][0] = 34030 (conocido como error tipo II)

A simple viste podemos deducir que si bien predice correctamente una alta cantidad de casos con estadia larga, el error tipo II es considerable y se debe tener en cuenta, ya que su interpretacion radica en que predice aproximadamente un tercio del total de datos como estadias cortas cuando en realidad tendrian que ser estadias largas.

# la primer metrica es la exactitud (accuracy) del modelo, mide el porcentaje de casos que el modelo ha acertado.
 
 (TP + TN) / (TP + FP + TN + FN) = 0.65 redondeado

# la segunda metrica es la precision del modelo, para medir la calidad del mismo. 
 
 ¿qué porcentaje de los que hemos dicho que son la clase positiva, en realidad lo son?

 TP / (TP + FP) = 0.64 redondeado

# y la tercer metrica es la exhaustividad del modelo, nos va a informar sobre la cantidad que el modelo es capaz de identificar
 
 ¿qué porcentaje de la clase positiva hemos sido capaces de identificar? 
 
 TP / (TP + FN) = 0.97 redondeado

## **Conclusion**

El estudio de las características y perfiles de los usuarios con el objetivo de predecir la ocupación hospitalaria, incluye a las siguientes variables que a criterio personal inciden mayoritariamente por sobre otras variables, lo cual no quiere decir que no se puedan estudiar otras y mejorar la prediccion.
     
    "Department_TB & Chest disease",
    "Department_anesthesia",
    "Age_51-60",
    "Age_61-70",
    "Age_71-80",
    "Age_81-90",
    "gender_Male"
​
El modelo desarrollado puede ayudar a administrar la demanda de camas en el hospital según la condición de los pacientes ingresados con una efectividad del 65%.
