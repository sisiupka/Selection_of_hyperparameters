# Selection of hyperparameters for machine learning models

## Описание задачи
Предлагается решить задачу бинарной классификации, а именно построить алгоритм, определяющий превысит ли средний заработок человека порог $50k. Каждый объект выборки — человек, для которого известны следующие признаки:
- age
- workclass
- fnlwgt
- education
- education-num
- marital-status
- occupation
- relationship
- race
- sex
- capital-gain
- capital-loss
- hours-per-week
Более подробно про признаки можно почитать [здесь](http://archive.ics.uci.edu/ml/machine-learning-databases/adult/adult.names). Целевой признак записан в переменной >50K,<=50K.

Мы будем оценивать качество моделей с помощью метрики AUC-ROC.

Сейчас и далее будем рассматривать 5 алгоритмов:
- KNN
- Decision Tree
- SGD Linear Classifier
- Random Forest
- Gradient Boosting
## Этапы работы
- Обучение классификаторов на вещественных признаках
- Масштабирование признаков
- Подбор комбинаций гиперпараметров
- Добавление категориальных признаков в модели
- Поиск новых полезных признаков c помощью создания полиномиальных признаков и их отбора посредством фильтрационных методов, жадного отбора признаков, встроенного в модель отбора признаков
- Смешивание моделей - Gradient Boosting и SGD Linear Classifier, показавших наилучшее качество на кросс-валидации
  
## Результаты подбора гиперпараметров
**Лучшие модели**: 
- GradientBoostingClassifier(n_estimators=159, criterion='friedman_mse', max_features='auto') с включением категориальных переменных, без
полиномиальных признаков.
ROC-AUC на кросс-валидации: 0.912
- SGDClassifier(loss='log', penalty='elasticnet') с включением категориальных переменных, без
полиномиальных признаков.
 ROC-AUC на кросс-валидации: 0.899
- RandomForestClassifier(n_estimators=53, criterion='entropy', max_features ='sqrt') с включением категориальных переменных, без
полиномиальных признаков.
 ROC-AUC на кросс-валидации: 0.894

