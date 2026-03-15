import { useState } from "react";

const menuData = {
  semaines: [
    {
      id: 1,
      jours: [
        {
          jour: "Lundi", calories: 1450,
          petitDej: { repas: "Porridge avoine + myrtilles + lait d'amande", cal: 310 },
          dejeuner: { repas: "Salade de poulet grillé, roquette, tomates, vinaigrette citron", cal: 420 },
          collation: { repas: "Pomme + 10 amandes", cal: 150 },
          diner: { repas: "Filet de cabillaud vapeur, brocolis, patate douce", cal: 380 },
          dessert: { repas: "Yaourt grec 0% + miel", cal: 120 },
        },
        {
          jour: "Mardi", calories: 1380,
          petitDej: { repas: "Œufs brouillés (2) + toast seigle + avocat", cal: 340 },
          dejeuner: { repas: "Soupe de lentilles corail + pain de seigle", cal: 380 },
          collation: { repas: "Carotte + houmous léger", cal: 110 },
          diner: { repas: "Dinde sautée aux légumes wok, quinoa", cal: 400 },
          dessert: { repas: "Orange", cal: 70 },
        },
        {
          jour: "Mercredi", calories: 1420,
          petitDej: { repas: "Smoothie banane-épinards-protéines + granola léger", cal: 320 },
          dejeuner: { repas: "Wrap dinde-crudités-moutarde ancienne", cal: 390 },
          collation: { repas: "Fromage blanc 0% + fraises", cal: 100 },
          diner: { repas: "Saumon en papillote, asperges, riz basmati", cal: 460 },
          dessert: { repas: "Compote sans sucre ajouté", cal: 70 },
        },
        {
          jour: "Jeudi", calories: 1400,
          petitDej: { repas: "Pain complet + beurre de cacahuète + café", cal: 290 },
          dejeuner: { repas: "Bowl riz brun, pois chiches rôtis, légumes grillés, tahini", cal: 450 },
          collation: { repas: "Kiwi + thé vert", cal: 60 },
          diner: { repas: "Escalope de veau, haricots verts, carottes vapeur", cal: 420 },
          dessert: { repas: "Mousse au café 0%", cal: 90 },
        },
        {
          jour: "Vendredi", calories: 1460,
          petitDej: { repas: "Pancakes protéinés avoine + sirop d'érable allégé", cal: 350 },
          dejeuner: { repas: "Salade niçoise légère (thon, œuf, haricots verts)", cal: 430 },
          collation: { repas: "Poignée de noix du Brésil + poire", cal: 140 },
          diner: { repas: "Crevettes sautées ail-citron, courgettes, boulgour", cal: 390 },
          dessert: { repas: "Framboises + yaourt grec", cal: 110 },
        },
        {
          jour: "Samedi", calories: 1500,
          petitDej: { repas: "Avocado toast + œuf poché + graines de sésame", cal: 400 },
          dejeuner: { repas: "Poulet tikka masala léger, riz basmati", cal: 490 },
          collation: { repas: "Edamame salé", cal: 100 },
          diner: { repas: "Salade cesar légère, filet de poulet", cal: 380 },
          dessert: { repas: "Sorbet citron (1 boule)", cal: 90 },
        },
        {
          jour: "Dimanche", calories: 1480,
          petitDej: { repas: "Granola maison + lait végétal + fruits rouges", cal: 360 },
          dejeuner: { repas: "Rôti de bœuf maigre, ratatouille, pommes de terre vapeur", cal: 500 },
          collation: { repas: "Infusion + 2 carrés chocolat noir 85%", cal: 70 },
          diner: { repas: "Velouté courgette-menthe + quiche légère au thon", cal: 410 },
          dessert: { repas: "Ananas frais", cal: 60 },
        },
      ],
    },
    {
      id: 2,
      jours: [
        {
          jour: "Lundi", calories: 1430,
          petitDej: { repas: "Flocons d'avoine + banane + cannelle", cal: 300 },
          dejeuner: { repas: "Taboulé de chou-fleur, feta allégée, tomates séchées", cal: 370 },
          collation: { repas: "Yaourt 0% + graines de chia", cal: 120 },
          diner: { repas: "Pavé de saumon, épinards à l'ail, lentilles vertes", cal: 480 },
          dessert: { repas: "Pamplemousse", cal: 60 },
        },
        {
          jour: "Mardi", calories: 1390,
          petitDej: { repas: "Toast complet + ricotta + concombre", cal: 270 },
          dejeuner: { repas: "Soupe minestrone maison + pain de seigle", cal: 360 },
          collation: { repas: "Céleri + sauce tzatziki légère", cal: 90 },
          diner: { repas: "Poulet rôti aux herbes, flageolets, carottes", cal: 430 },
          dessert: { repas: "Compote pomme-poire sans sucre", cal: 80 },
        },
        {
          jour: "Mercredi", calories: 1440,
          petitDej: { repas: "Smoothie bowl mangue-ananas + amandes effilées", cal: 330 },
          dejeuner: { repas: "Salade de quinoa, avocat, betterave, graines de courge", cal: 430 },
          collation: { repas: "Pomme + 1 C.S de beurre d'amande", cal: 150 },
          diner: { repas: "Filet de truite, purée de céleri-rave, haricots", cal: 390 },
          dessert: { repas: "Kiwi + menthe fraîche", cal: 50 },
        },
        {
          jour: "Jeudi", calories: 1410,
          petitDej: { repas: "Œuf à la coque + mouillettes seigle + thé", cal: 250 },
          dejeuner: { repas: "Curry de pois chiches léger, chou-fleur, riz", cal: 450 },
          collation: { repas: "Poignée de myrtilles + café", cal: 60 },
          diner: { repas: "Rôti de dinde, brocolis, courgettes", cal: 400 },
          dessert: { repas: "Fromage blanc 0% + vanille", cal: 90 },
        },
        {
          jour: "Vendredi", calories: 1470,
          petitDej: { repas: "Crêpe protéinée + fruits rouges + miel", cal: 320 },
          dejeuner: { repas: "Poke bowl saumon, edamame, riz, concombre", cal: 490 },
          collation: { repas: "Noix de cajou (petite poignée)", cal: 130 },
          diner: { repas: "Omelette légumes + salade verte", cal: 330 },
          dessert: { repas: "Yaourt grec + fraises", cal: 100 },
        },
        {
          jour: "Samedi", calories: 1510,
          petitDej: { repas: "Bagel complet + saumon fumé + cream cheese allégé", cal: 420 },
          dejeuner: { repas: "Steak haché 5% + ratatouille + riz complet", cal: 470 },
          collation: { repas: "Smoothie vert concombre-gingembre", cal: 80 },
          diner: { repas: "Salade composée crevettes-avocat-pamplemousse", cal: 410 },
          dessert: { repas: "Sorbet framboise (1 boule)", cal: 80 },
        },
        {
          jour: "Dimanche", calories: 1490,
          petitDej: { repas: "Tartines pain complet + œufs mimosa léger + tomates", cal: 370 },
          dejeuner: { repas: "Gigot d'agneau maigre, légumes du four, semoule", cal: 510 },
          collation: { repas: "Tisane + 2 dattes + amandes", cal: 90 },
          diner: { repas: "Velouté potimarron + salade chèvre-noix légère", cal: 380 },
          dessert: { repas: "Compote rhubarbe sans sucre", cal: 50 },
        },
      ],
    },
    {
      id: 3,
      jours: [
        {
          jour: "Lundi", calories: 1420,
          petitDej: { repas: "Muesli non sucré + lait écrémé + noisettes", cal: 310 },
          dejeuner: { repas: "Salade de lentilles, poivrons grillés, feta", cal: 400 },
          collation: { repas: "Poire + thé vert", cal: 70 },
          diner: { repas: "Blanc de volaille en croûte d'herbes, brocolis, patate douce", cal: 430 },
          dessert: { repas: "Yaourt nature 0% + coulis framboise", cal: 110 },
        },
        {
          jour: "Mardi", calories: 1400,
          petitDej: { repas: "Pain de seigle + houmous + radis", cal: 270 },
          dejeuner: { repas: "Bouillon miso + tofu + légumes + riz", cal: 390 },
          collation: { repas: "Concombre + guacamole léger", cal: 120 },
          diner: { repas: "Sardines grillées, salade de fenouil-orange", cal: 390 },
          dessert: { repas: "Abricots secs (3) + tisane", cal: 60 },
        },
        {
          jour: "Mercredi", calories: 1450,
          petitDej: { repas: "Porridge sarrasin + pomme râpée + cannelle", cal: 330 },
          dejeuner: { repas: "Bowl buddha : tofu rôti, avocat, chou rouge, sésame", cal: 460 },
          collation: { repas: "Fromage blanc 0% + fruits de saison", cal: 100 },
          diner: { repas: "Lieu noir vapeur, asperges vertes, boulgour", cal: 400 },
          dessert: { repas: "Gelée de fruits maison", cal: 60 },
        },
        {
          jour: "Jeudi", calories: 1380,
          petitDej: { repas: "Œufs cocotte tomates + pain de campagne", cal: 290 },
          dejeuner: { repas: "Gaspacho + quiche lorraine allégée", cal: 380 },
          collation: { repas: "Cerises ou raisin (petite grappe)", cal: 80 },
          diner: { repas: "Lapin moutarde-thym, haricots verts, carottes", cal: 420 },
          dessert: { repas: "Mousse au citron légère", cal: 80 },
        },
        {
          jour: "Vendredi", calories: 1460,
          petitDej: { repas: "Tartines complet + ricotta + figues fraîches", cal: 340 },
          dejeuner: { repas: "Pâtes complètes au pesto maison, tomates cerises, roquette", cal: 470 },
          collation: { repas: "Shake protéiné vanille", cal: 130 },
          diner: { repas: "Roulades de sole aux crevettes, poireaux, quinoa", cal: 380 },
          dessert: { repas: "Coulis de fruits rouges + yaourt", cal: 90 },
        },
        {
          jour: "Samedi", calories: 1500,
          petitDej: { repas: "Waffles avoine-banane + sirop allégé", cal: 380 },
          dejeuner: { repas: "Tajine de poulet aux légumes, couscous complet", cal: 500 },
          collation: { repas: "Thé à la menthe + orange", cal: 70 },
          diner: { repas: "Pizza légère sur pita : mozzarella allégée, légumes", cal: 410 },
          dessert: { repas: "Sorbet passion (1 boule)", cal: 80 },
        },
        {
          jour: "Dimanche", calories: 1470,
          petitDej: { repas: "Brunch œufs bénédictine allégée + salade verte", cal: 420 },
          dejeuner: { repas: "Côte de veau, gratin de chou-fleur léger, carottes", cal: 490 },
          collation: { repas: "Thé + 2 carrés chocolat noir", cal: 70 },
          diner: { repas: "Soupe de légumes maison + tartine au chèvre", cal: 380 },
          dessert: { repas: "Pomme cuite cannelle", cal: 80 },
        },
      ],
    },
    {
      id: 4,
      jours: [
        {
          jour: "Lundi", calories: 1430,
          petitDej: { repas: "Flocons d'avoine + lait végétal + graines de lin", cal: 300 },
          dejeuner: { repas: "Salade composée : poulpe, pommes de terre, olives", cal: 410 },
          collation: { repas: "Amandes (15g) + thé vert", cal: 90 },
          diner: { repas: "Filet de poulet mariné au citron, couscous léger", cal: 440 },
          dessert: { repas: "Yaourt 0% + coulis mangue", cal: 100 },
        },
        {
          jour: "Mardi", calories: 1400,
          petitDej: { repas: "Pain de seigle + œuf dur + tomate", cal: 260 },
          dejeuner: { repas: "Soupe potiron-gingembre + tartine complet", cal: 350 },
          collation: { repas: "Banane petite + fromage blanc", cal: 150 },
          diner: { repas: "Moules marinières, frites de panais au four", cal: 440 },
          dessert: { repas: "Salade de fruits de saison", cal: 80 },
        },
        {
          jour: "Mercredi", calories: 1450,
          petitDej: { repas: "Acai bowl + granola léger + kiwi", cal: 350 },
          dejeuner: { repas: "Wrap au saumon fumé, crudités, crème légère", cal: 400 },
          collation: { repas: "Edamame + infusion", cal: 100 },
          diner: { repas: "Émincé de bœuf maigre, poivrons, riz complet", cal: 430 },
          dessert: { repas: "Fromage blanc 0% + fruits rouges", cal: 100 },
        },
        {
          jour: "Jeudi", calories: 1420,
          petitDej: { repas: "Chia pudding lait coco léger + ananas", cal: 310 },
          dejeuner: { repas: "Salade grecque + pain pita complet", cal: 420 },
          collation: { repas: "Pêche ou nectarine", cal: 70 },
          diner: { repas: "Rôti de veau, petits pois, carottes glacées", cal: 460 },
          dessert: { repas: "Compote cerise sans sucre", cal: 70 },
        },
        {
          jour: "Vendredi", calories: 1480,
          petitDej: { repas: "Crêpe sarrasin + œuf + jambon blanc", cal: 360 },
          dejeuner: { repas: "Sushi/maki maison léger + soupe miso", cal: 440 },
          collation: { repas: "Yaourt grec + noix", cal: 140 },
          diner: { repas: "Bar en papillote, fenouil, citron confit, semoule", cal: 400 },
          dessert: { repas: "Sorbet citron vert (1 boule)", cal: 80 },
        },
        {
          jour: "Samedi", calories: 1510,
          petitDej: { repas: "Brunch léger : tartines saumon, fromage blanc, tomates", cal: 380 },
          dejeuner: { repas: "Lasagnes légères courgette-ricotta-tomates", cal: 490 },
          collation: { repas: "Thé glacé maison + fruits frais", cal: 90 },
          diner: { repas: "Salade lentilles-magret fumé (en petite quantité)", cal: 410 },
          dessert: { repas: "Mousse mangue légère", cal: 90 },
        },
        {
          jour: "Dimanche", calories: 1480,
          petitDej: { repas: "Pain perdu light + fruits rouges + café", cal: 370 },
          dejeuner: { repas: "Poulet fermier rôti, gratin dauphinois allégé, salade", cal: 510 },
          collation: { repas: "Carré de chocolat noir + herbal tea", cal: 70 },
          diner: { repas: "Velouté poireau-pomme de terre léger + œuf poché", cal: 390 },
          dessert: { repas: "Ananas rôti vanille-cannelle", cal: 80 },
        },
      ],
    },
  ],
};

const repasIcons = {
  petitDej: "☀️",
  dejeuner: "🍽️",
  collation: "🍎",
  diner: "🌙",
  dessert: "🍮",
};

const repasLabels = {
  petitDej: "Petit-déj",
  dejeuner: "Déjeuner",
  collation: "Collation",
  diner: "Dîner",
  dessert: "Dessert",
};

const getCalColor = (cal) => {
  if (cal < 1400) return "#6ee7b7";
  if (cal < 1460) return "#fcd34d";
  return "#f9a8d4";
};

export default function MenuPlanning() {
  const [selectedWeek, setSelectedWeek] = useState(0);
  const [selectedDay, setSelectedDay] = useState(null);
  const [expandedRepas, setExpandedRepas] = useState(null);

  const semaine = menuData.semaines[selectedWeek];
  const jour = selectedDay !== null ? semaine.jours[selectedDay] : null;

  const totalCal = semaine.jours.reduce((a, b) => a + b.calories, 0);
  const avgCal = Math.round(totalCal / 7);

  return (
    <div style={{
      minHeight: "100vh",
      background: "linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #0f172a 100%)",
      fontFamily: "'Georgia', serif",
      padding: "0",
      overflowX: "hidden",
    }}>
      {/* Header */}
      <div style={{
        background: "linear-gradient(90deg, #065f46 0%, #0d9488 50%, #065f46 100%)",
        padding: "32px 24px 24px",
        textAlign: "center",
        borderBottom: "2px solid #14b8a6",
        position: "relative",
        overflow: "hidden",
      }}>
        <div style={{
          position: "absolute", top: 0, left: 0, right: 0, bottom: 0,
          background: "repeating-linear-gradient(45deg, transparent, transparent 20px, rgba(255,255,255,0.02) 20px, rgba(255,255,255,0.02) 40px)",
        }} />
        <div style={{ position: "relative", zIndex: 1 }}>
          <div style={{ fontSize: "11px", letterSpacing: "4px", color: "#6ee7b7", textTransform: "uppercase", marginBottom: "8px" }}>
            Programme Nutritionnel
          </div>
          <h1 style={{
            fontSize: "clamp(24px, 5vw, 42px)", color: "#f0fdf4", margin: "0 0 8px",
            fontWeight: "normal", letterSpacing: "1px",
          }}>
            Menu Déficit Calorique
          </h1>
          <p style={{ color: "#6ee7b7", fontSize: "14px", margin: 0 }}>
            ~1 400–1 500 kcal/jour · 4 semaines complètes
          </p>
        </div>
      </div>

      {/* Info Banner */}
      <div style={{
        display: "flex", gap: "12px", justifyContent: "center", flexWrap: "wrap",
        padding: "16px 20px", background: "rgba(20,184,166,0.05)",
        borderBottom: "1px solid rgba(20,184,166,0.2)",
      }}>
        {[
          { label: "Objectif calorique", val: "1 400–1 500 kcal" },
          { label: "Déficit estimé", val: "~500 kcal/j" },
          { label: "Perte visée", val: "~0,5 kg/semaine" },
          { label: "Durée", val: "4 semaines" },
        ].map(({ label, val }) => (
          <div key={label} style={{
            background: "rgba(6,95,70,0.3)", border: "1px solid rgba(20,184,166,0.3)",
            borderRadius: "8px", padding: "10px 18px", textAlign: "center",
          }}>
            <div style={{ fontSize: "11px", color: "#6ee7b7", letterSpacing: "2px", textTransform: "uppercase" }}>{label}</div>
            <div style={{ fontSize: "16px", color: "#f0fdf4", fontWeight: "bold", marginTop: "4px" }}>{val}</div>
          </div>
        ))}
      </div>

      <div style={{ maxWidth: "960px", margin: "0 auto", padding: "24px 16px" }}>

        {/* Week Selector */}
        <div style={{ display: "flex", gap: "10px", marginBottom: "24px", justifyContent: "center", flexWrap: "wrap" }}>
          {menuData.semaines.map((s, i) => (
            <button key={i} onClick={() => { setSelectedWeek(i); setSelectedDay(null); }} style={{
              padding: "10px 22px",
              background: selectedWeek === i ? "#0d9488" : "rgba(6,95,70,0.2)",
              border: selectedWeek === i ? "2px solid #14b8a6" : "2px solid rgba(20,184,166,0.3)",
              borderRadius: "50px", color: selectedWeek === i ? "#f0fdf4" : "#6ee7b7",
              cursor: "pointer", fontSize: "14px", fontFamily: "Georgia, serif",
              transition: "all 0.2s",
              fontWeight: selectedWeek === i ? "bold" : "normal",
            }}>
              Semaine {s.id}
            </button>
          ))}
        </div>

        {/* Weekly Summary */}
        <div style={{
          background: "rgba(6,95,70,0.15)", border: "1px solid rgba(20,184,166,0.2)",
          borderRadius: "12px", padding: "14px 20px", marginBottom: "20px",
          display: "flex", justifyContent: "space-between", alignItems: "center", flexWrap: "wrap", gap: "8px",
        }}>
          <span style={{ color: "#6ee7b7", fontSize: "13px" }}>
            Semaine {semaine.id} · Moyenne journalière
          </span>
          <span style={{ color: "#f0fdf4", fontSize: "20px", fontWeight: "bold" }}>
            {avgCal} kcal/jour
          </span>
          <span style={{ color: "#6ee7b7", fontSize: "13px" }}>
            Total semaine : {totalCal} kcal
          </span>
        </div>

        {/* Day Cards Grid */}
        <div style={{
          display: "grid",
          gridTemplateColumns: "repeat(auto-fill, minmax(120px, 1fr))",
          gap: "10px", marginBottom: "24px",
        }}>
          {semaine.jours.map((j, i) => (
            <button key={i} onClick={() => setSelectedDay(selectedDay === i ? null : i)} style={{
              background: selectedDay === i
                ? "rgba(20,184,166,0.25)"
                : "rgba(6,95,70,0.15)",
              border: selectedDay === i
                ? "2px solid #14b8a6"
                : "2px solid rgba(20,184,166,0.2)",
              borderRadius: "10px", padding: "14px 8px",
              cursor: "pointer", transition: "all 0.2s",
              textAlign: "center",
            }}>
              <div style={{ color: "#6ee7b7", fontSize: "11px", letterSpacing: "1px", textTransform: "uppercase", marginBottom: "6px" }}>{j.jour}</div>
              <div style={{
                fontSize: "15px", fontWeight: "bold",
                color: getCalColor(j.calories),
                marginBottom: "4px",
              }}>{j.calories}</div>
              <div style={{ color: "#94a3b8", fontSize: "10px" }}>kcal</div>
            </button>
          ))}
        </div>

        {/* Day Detail */}
        {jour && (
          <div style={{
            background: "rgba(6,95,70,0.12)",
            border: "1px solid rgba(20,184,166,0.3)",
            borderRadius: "14px", overflow: "hidden",
            animation: "fadeIn 0.3s ease",
          }}>
            <style>{`@keyframes fadeIn { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: translateY(0); } }`}</style>
            <div style={{
              background: "linear-gradient(90deg, rgba(6,95,70,0.5), rgba(13,148,136,0.3))",
              padding: "16px 24px",
              display: "flex", justifyContent: "space-between", alignItems: "center",
              borderBottom: "1px solid rgba(20,184,166,0.2)",
            }}>
              <div>
                <div style={{ color: "#6ee7b7", fontSize: "11px", letterSpacing: "3px", textTransform: "uppercase" }}>Semaine {semaine.id}</div>
                <div style={{ color: "#f0fdf4", fontSize: "24px", fontWeight: "bold" }}>{jour.jour}</div>
              </div>
              <div style={{ textAlign: "right" }}>
                <div style={{ color: getCalColor(jour.calories), fontSize: "28px", fontWeight: "bold" }}>{jour.calories}</div>
                <div style={{ color: "#6ee7b7", fontSize: "12px" }}>kcal total</div>
              </div>
            </div>

            <div style={{ padding: "16px 20px" }}>
              {Object.keys(repasIcons).map((key) => {
                const item = jour[key];
                const isOpen = expandedRepas === key;
                return (
                  <div key={key} style={{ marginBottom: "8px" }}>
                    <div
                      onClick={() => setExpandedRepas(isOpen ? null : key)}
                      style={{
                        display: "flex", alignItems: "center", gap: "12px",
                        padding: "12px 16px",
                        background: isOpen ? "rgba(20,184,166,0.15)" : "rgba(255,255,255,0.03)",
                        borderRadius: "8px", cursor: "pointer",
                        border: "1px solid " + (isOpen ? "rgba(20,184,166,0.4)" : "rgba(255,255,255,0.06)"),
                        transition: "all 0.2s",
                      }}>
                      <span style={{ fontSize: "18px" }}>{repasIcons[key]}</span>
                      <div style={{ flex: 1 }}>
                        <div style={{ color: "#6ee7b7", fontSize: "10px", letterSpacing: "2px", textTransform: "uppercase" }}>{repasLabels[key]}</div>
                        <div style={{ color: "#e2e8f0", fontSize: "13px", marginTop: "2px" }}>{item.repas}</div>
                      </div>
                      <div style={{ color: "#fcd34d", fontSize: "13px", fontWeight: "bold", whiteSpace: "nowrap" }}>
                        {item.cal} kcal
                      </div>
                    </div>
                  </div>
                );
              })}

              {/* Calorie Bar */}
              <div style={{ marginTop: "16px", padding: "12px 16px", background: "rgba(0,0,0,0.2)", borderRadius: "8px" }}>
                <div style={{ display: "flex", justifyContent: "space-between", marginBottom: "8px" }}>
                  <span style={{ color: "#94a3b8", fontSize: "12px" }}>Progression calorique</span>
                  <span style={{ color: "#fcd34d", fontSize: "12px" }}>{jour.calories} / 1500 kcal</span>
                </div>
                <div style={{ height: "8px", background: "rgba(255,255,255,0.1)", borderRadius: "4px", overflow: "hidden" }}>
                  <div style={{
                    height: "100%",
                    width: `${Math.min((jour.calories / 1500) * 100, 100)}%`,
                    background: "linear-gradient(90deg, #0d9488, #14b8a6)",
                    borderRadius: "4px", transition: "width 0.5s ease",
                  }} />
                </div>
              </div>
            </div>
          </div>
        )}

        {!jour && (
          <div style={{
            textAlign: "center", padding: "32px",
            color: "#6ee7b7", fontSize: "14px",
            border: "1px dashed rgba(20,184,166,0.3)", borderRadius: "12px",
          }}>
            👆 Cliquez sur un jour pour voir le détail du menu
          </div>
        )}

        {/* Légende */}
        <div style={{
          marginTop: "24px", padding: "16px 20px",
          background: "rgba(0,0,0,0.2)", borderRadius: "10px",
          display: "flex", gap: "20px", flexWrap: "wrap", justifyContent: "center",
        }}>
          <span style={{ color: "#94a3b8", fontSize: "12px", letterSpacing: "1px" }}>LÉGENDE :</span>
          {[
            { color: "#6ee7b7", label: "< 1 400 kcal · Léger" },
            { color: "#fcd34d", label: "1 400–1 460 kcal · Équilibré" },
            { color: "#f9a8d4", label: "> 1 460 kcal · Repas social" },
          ].map(({ color, label }) => (
            <div key={label} style={{ display: "flex", alignItems: "center", gap: "6px" }}>
              <div style={{ width: "10px", height: "10px", borderRadius: "50%", background: color }} />
              <span style={{ color: "#94a3b8", fontSize: "12px" }}>{label}</span>
            </div>
          ))}
        </div>

        {/* Footer tip */}
        <div style={{
          marginTop: "20px", padding: "14px 18px",
          background: "rgba(6,95,70,0.2)", border: "1px solid rgba(20,184,166,0.2)",
          borderRadius: "10px", textAlign: "center",
        }}>
          <p style={{ color: "#6ee7b7", fontSize: "12px", margin: 0, lineHeight: "1.7" }}>
            💧 Boire 1,5 à 2L d'eau par jour · 🧂 Limiter le sel · 🍷 Alcool à éviter pendant le déficit<br />
            ⚠️ Ces menus sont indicatifs. Consultez un professionnel de santé pour un suivi personnalisé.
          </p>
        </div>
      </div>
    </div>
  );
}
