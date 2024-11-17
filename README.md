# Долгосрочное прогнозирование характеристик стока рек Арктической зоны на примере реки Колыма

____

## Оглавление

0. [Введение](#Введение)
1. [Разметка данных. Формирование датасета](#Разметкаданных.Формированиедатасета)
2. [Выбор моделей](#Выбор-моделей)
3. [Итоги](#Итоги)
4. [Ссылки](#Ссылки)

 ____

 
 ## Введение
Настоящий проект посвящен разработке методики долгосрочного прогнозирования среднемесячного уровня воды реки Колыма с заблаговременностью месяц. Для достижения этой цели были использованы временные ряды гидрометеорологических данных суточного разрешения за период с 1985 по 2019 гг. В работе были реализованы и сравнены эффективности четырех моделей: SARIMAX, рекуррентные нейронные сети LSTM и GRU, а также модель LS-SVM. Особое внимание уделено оценке качества прогнозов на независимой выборке данных за период с 2011 по 2019 гг. Полученные результаты имеют важное практическое значение для эффективного управления водными ресурсами в регионе, предотвращения и смягчения последствий опасных гидрологических явлений, а также для обеспечения безопасного водопользования и судоходства на реке Колыма.

 ## Разметка данных. Формирование датасета
 
Для исследования были использованы гидрометеорологические данные разрешением 1 месяц, осредненные по суточным данным и полученные из базы данных Гидрометцентра России и архивов ВНИИГМИ МЦД. В качестве предиктора был выбран среднемесячный уровень воды на гидрологическом посту г. Среднеколымск, находящимся в верхнем течении реки. Анализ качества работы модели проводился на периоде с 2011 по 2019 гг., который включал в себя многоводные и маловодные года. В процессе разработки моделей нейронных сетей были выделены обучающая (1985-2003 гг.), валидационная (2004-2010 гг.) и тестовая (2011-2019 гг.) выборки.

Для выбранного гидрологического поста были подготовлены данные суточного разрешения об уровне воды с 1985 по 2019 гг. С помощью технологий географических информационных систем был выделен водосборный бассейн и определено 11 метеостанций на его территории. Из этих метеостанций удалось получить данные только по 9 метеостанциям, информация о которых была доступна в архивах ВНИИГМИ-МЦД.  На основе данных этих метеостанций были подготовлены временные ряды суточного разрешения, включающие информацию о температуре и влажности воздуха, скорости ветра, суммарном количестве осадков, а также высоте снежного покрова для каждой метеостанции отдельно, а также ряды осредненной по водосбору метеорологической информации за 1960 – 2020 гг. 

В силу того, что данные суточного разрешения по каждой метеостанции имели свои периоды пропусков в данных, местами достаточно продолжительные, в итоге было решено использовать осредненную по всем метеостанциям информацию.

## Выбор моделей
Анализ российского и советского опыта в развитии методов долгосрочного прогнозирования с прогнозом заблаговременностью месяц и более длительный период показал, что они практически не развиваются с начала 30-х гг прошлого столетия. Вплоть до настоящего времени в оперативной практике Росгидромета долгосрочные прогнозы характеристик весеннего стока используют физико-статистический подход, включающий корреляционные методы анализа, и фактически представляют из себя множественную регрессию: соотношение между прогнозируемой величиной и набором показателей, характеризующих состояние водосбора за разные промежутки времени перед началом снеготаяния ([1-6]).
В то время анализ зарубежной литературы показал, что в последнее время все чаще для долгосрочного прогнозирования используют более современные методы, в том числе и методы машинного обучения и глубоких нейронных сетей ([7-9]). 

Потому в ходе исследования было решено реализовать несколько различных моделей, представляющий из себя как классический советский подход, так и с использованием методов нейронных сетей. 


## Итоги

Произведена качественная и детальная ручная разметка нескольких разнообразных гистологий свиной печени для последующего обучения нейросети. Создан алгоритм на базе нейросети resnet-18, способный с высокой точностью (более 97%) определять зоны, подвергшиеся механическому разрушению в результате воздействия высокоинтенсивного фокусированного ультразвукового пучка, предсказать площадь области разрушения и правильно восстановить геометрию этой области. Алгоритм способен определять области разрушения с высокой детализацией, что делает его эффективным инструментом анализа гистологических изображений. Результаты исследования будут использованы для определения того, как режим облучения влияет на степень и характер механического разрушения тканей. Это исследование позволит определить восприимчивость различных типов тканей к такому воздействию и подобрать оптимальные параметры для неинвазивного разрушения опухолей, а определение связи между характером механического разрушения тканей и параметрами импульсного ультразвукового облучения позволит контролировать безопасность и эффективность методов гистотрипсии. 

## Ссылки

1.	T.D. Khokhlova, et al. JASA, 130(5):3498–3510, 2011
2.	J.C. Simon, et al. Phys Med Biol 57 8061–8078, 2021
3.	Homeyer A., Schenk A., Arlt J., Dahmen U., Dirsch O., Hahn H.K. (2013). Practical quantification of necrosis in histological whole-slide images, Computerized Medical Imaging and Graphics, 37(4), 313-322.
4.	Brady L., Wang Y. N., Rombokas E., Ledoux W. R. (2021). Comparison of texture-based classification and deep learning for plantar soft tissue histology segmentation. Computers in Biology and Medicine, 104491.
5.	Wei J. W., Tafe L. J., Linnik Y. A., Vaickus L. J., Tomita N.,  Hassanpour S. (2019). Pathologist-level classification of histologic patterns on resected lung adenocarcinoma slides with deep neural networks. Scientific reports, 9(1), 1-8.
6.	Iizuka O., Kanavati F., Kato K., Rambeau M., Arihiro K., Tsuneki M. (2020). Deep learning models for histopathological classification of gastric and colonic epithelial tumours. Scientific reports, 10(1), 1-11.
7.	https://github.com/akrokhmal/histology_segmentation 
8.	Гистологические изображения https://drive.google.com/drive/folders/1K7BbjFaPSDk4xhtRUau5RZGhMwslTkOg?usp=sharing
9.	Сегментация гистологических изображений https://drive.google.com/drive/folders/176wQ9hVBx23etjerM36CNIqn7zW_7oYs?usp=sharing 
10.	Датасет из 80-пиксельных фрагментов гистологий https://drive.google.com/file/d/1CX7_9CCkOu7EKSAyPTPB5HDrDxa-BU05/view?usp=sharing 
11.	Веса модели resnet-18 для датасета из 80-пиксельных фрагментов https://drive.google.com/file/d/1INQezpgeoHZ1aPJ4WQ1wFkIH34sI7Z_V/view?usp=sharing 
12.	Датасет из 256-пиксельных фрагментов гистологий https://drive.google.com/file/d/1Xq3ztV7wAXx3DPzJ8sAWPX2aCAMIIbP6/view?usp=sharing 
13.	Веса модели resnet-18 для датасета из 256-пиксельных фрагментов https://drive.google.com/file/d/107KdhNkixkQjARVnXvy6aN_PE5erIWhq/view?usp=sharing 
14.	Предсказания нейросети при разбиении изображения на 80-пиксельные фрагменты https://drive.google.com/drive/folders/1puh7qqkoDURz8eJX-bKG5fzrblbrfpU4?usp=sharing 
15.	Предсказания нейросети при разбиении изображения на 256-пиксельные фрагменты https://drive.google.com/drive/folders/12cPh2CPOSM9Z1R_WKHNfGY0cKMDsOF1H?usp=sharing 
16.	Результат сегментации при комбинации результатов предсказаний двух нейросетей https://drive.google.com/drive/folders/1MIYUHEpWnIliv6kjigXXY6L5nclYXL0Z?usp=sharing 

