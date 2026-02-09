/*CREATE OR REPLACE VIEW vw_ventas_mensuales AS
SELECT 
    d.año,
    d.mes,
    d.nombre_mes,

    -- Fecha representativa del mes (clave para Power BI)
    MAKE_DATE(d.año, d.mes, 1) AS fecha_mes,

    -- Métricas
    SUM(v.total) AS ventas_mes,

    LAG(SUM(v.total)) OVER (
        ORDER BY d.año, d.mes
    ) AS ventas_mes_anterior,

    ROUND(
        (SUM(v.total) - LAG(SUM(v.total)) OVER (ORDER BY d.año, d.mes))
        / NULLIF(LAG(SUM(v.total)) OVER (ORDER BY d.año, d.mes), 0) * 100,
        2
    ) AS variacion_pct

FROM ventas v
JOIN dim_fecha d
    ON v.fecha = d.fecha

GROUP BY 
    d.año,
    d.mes,
    d.nombre_mes;

*/
SELECT * FROM vw_ventas_mensuales;
