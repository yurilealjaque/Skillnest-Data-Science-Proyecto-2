# Análisis Inicial y Selección de Problema

## Descripción
Este proyecto tiene como objetivo realizar un análisis exploratorio de datos (EDA) sobre distintos conjuntos de datos para identificar sus características, calidad y posibles desafíos. A partir de este análisis, se selecciona un conjunto de datos y una problemática específica para desarrollar en etapas posteriores, justificando su relevancia y potencial de aplicación en técnicas de ciencia de datos y aprendizaje automático.

| Dataset | Problema que resuelve | Tipo de problema | Valor para empresa/sociedad | Ventajas | Riesgos o debilidades |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Credit Risk** | Predecir si una persona puede caer en impago de un préstamo | Clasificación binaria | Alto valor empresarial para bancos, fintech o cooperativas | Variable objetivo clara: default; tamaño manejable; columnas financieras fáciles de explicar | Tiene licencia no comercial; tema sensible porque puede afectar decisiones de crédito |
| **AI Impact Jobs 2030** | Analizar cómo la IA podría afectar empleos, industrias y habilidades hacia 2030 | Clasificación, regresión o EDA predictivo | Alto valor social y educativo | Tema actual, llamativo y con buena narrativa | Puede ser especulativo o sintético; difícil defender conclusiones como hechos reales |
| **Tourism Recommendation** | Recomendar destinos turísticos según perfil, comportamiento y contexto del usuario | Sistemas de recomendación / clusterización | Alto valor empresarial para turismo, apps y agencias | Muy interesante y moderno; permite recomendación personalizada | Puede ser más complejo que lo necesario; requiere entender recomendadores, usuarios, interacciones y contexto |
| **Hospital Readmission Risk** | Predecir pacientes con riesgo de reingreso hospitalario dentro de 30 días | Clasificación binaria | Muy alto valor social y sanitario | Propósito social muy fuerte; variable objetivo clara: readmitted; muchas variables clínicas útiles | Puede ser más delicado por ser salud; muchas columnas; puede requerir explicación ética y clínica cuidadosa |

## Conclusión final, segunda parte del proyecto

En esta segunda parte del proyecto se construyó un flujo completo de preprocesamiento y modelado para el dataset Credit Risk. Se utilizaron pipelines de `sklearn` para integrar imputación, escalado, codificación de variables categóricas y entrenamiento de modelos de clasificación.

Inicialmente se compararon distintos modelos: Regresión Logística, KNN, Árbol de Decisión y Random Forest. La comparación mediante validación cruzada mostró que la Regresión Logística tenía un buen desempeño inicial, especialmente en F1-score y ROC-AUC.

Posteriormente, se optimizó la Regresión Logística mediante `GridSearchCV`, obteniendo como mejores hiperparámetros `C = 0.1` y `solver = liblinear`. También se optimizó Random Forest mediante `RandomizedSearchCV`, logrando una mejora en algunas métricas generales.

Al comparar ambos modelos optimizados en el conjunto de prueba, Random Forest obtuvo mejor accuracy y ROC-AUC, mientras que la Regresión Logística obtuvo mejor recall para la clase `default = yes`. Dado que en un problema de riesgo crediticio es más importante detectar clientes que podrían caer en incumplimiento, se selecciona la Regresión Logística optimizada como modelo final.

Como limitación, el dataset cuenta con solo 1000 registros, por lo que existe riesgo de sobreajuste y sería recomendable validar el modelo con más datos en un contexto real. Además, podrían explorarse técnicas adicionales como ajuste de umbral, balanceo de clases u optimización avanzada con Optuna.