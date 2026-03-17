# Landing-Page
Gas power transitioning forum landing page
import { useState } from "react";

export default function GasTransitionForumLandingPage() {
  const [formData, setFormData] = useState({
    fullName: "",
    phone: "",
    email: "",
    jobTitle: "",
    businessName: "",
    industry: "",
    location: "",
    generatorSize: "",
    generatorCount: "",
    usageFrequency: "",
    hoursPerDay: "",
    monthlyDieselSpend: "",
    decisionMaker: "",
    transitionTimeline: "",
    painPoints: [],
    challenges: "",
    consultation: "",
  });

  const [submitted, setSubmitted] = useState(false);

  const eventDateISO = "20260423T110000";
  const eventEndDateISO = "20260423T140000";
  const calendarUrl = `https://calendar.google.com/calendar/render?action=TEMPLATE&text=${encodeURIComponent("Gas Transitioning Forum 2026")}&dates=${eventDateISO}/${eventEndDateISO}&details=${encodeURIComponent("Join the Gas Transitioning Forum to explore practical pathways for moving from diesel generators to gas-powered energy solutions.")}&location=${encodeURIComponent("Ibadan Business School, Francis Okediji Street, off Adeyi Avenue, Old Bodija, Ibadan")}`;
  const whatsappUrl = `https://wa.me/2349160723000?text=${encodeURIComponent("Hello, I would like to make an enquiry about the Gas Transitioning Forum 2026.")}`;

  const painPointOptions = [
    "High diesel cost",
    "Unstable fuel supply",
    "Frequent maintenance",
    "Noise and disruption",
    "Downtime and poor reliability",
    "Fuel theft or leakage",
    "Emissions and sustainability pressure",
    "Scaling power cost as business grows",
  ];

  const handleChange = (field, value) => {
    setFormData((prev) => ({ ...prev, [field]: value }));
  };

  const handleCheckbox = (value) => {
    setFormData((prev) => ({
      ...prev,
      painPoints: prev.painPoints.includes(value)
        ? prev.painPoints.filter((item) => item !== value)
        : [...prev.painPoints, value],
    }));
  };

  const handleSubmit = (e) => {
    e.preventDefault();

    const payload = {
      ...formData,
      submittedAt: new Date().toISOString(),
      leadScoreHint:
        formData.decisionMaker === "Yes" &&
        ["Immediately", "Within 3 months"].includes(formData.transitionTimeline)
          ? "High Intent"
          : "Standard Intent",
    };

    console.log("Submit to CRM / Airtable / webhook:", payload);
    setSubmitted(true);
  };

  if (submitted) {
    return (
      <div className="min-h-screen bg-[radial-gradient(circle_at_top,_rgba(250,204,21,0.18),_transparent_30%),linear-gradient(to_bottom,_#0f172a,_#111827)] px-6 py-10 text-white">
        <div className="mx-auto flex min-h-[85vh] max-w-3xl items-center justify-center">
          <div className="w-full rounded-[32px] border border-white/10 bg-white/5 p-8 text-center shadow-2xl backdrop-blur md:p-12">
            <div className="mx-auto mb-6 flex h-16 w-16 items-center justify-center rounded-full bg-emerald-500/20 text-3xl">
              ✓
            </div>
            <p className="text-sm font-semibold uppercase tracking-[0.18em] text-amber-300">Registration received</p>
            <h1 className="mt-4 text-3xl font-bold tracking-tight md:text-4xl">
              You have successfully reserved your seat.
            </h1>
            <p className="mx-auto mt-4 max-w-2xl text-base leading-7 text-slate-300 md:text-lg">
              Thank you for registering for the Gas Transitioning Forum. Our team will review your energy profile and reach out with event details and any relevant follow-up before the forum.
            </p>
            <div className="mt-8 grid gap-4 text-left sm:grid-cols-2">
              <div className="rounded-2xl border border-white/10 bg-black/20 p-5">
                <p className="text-sm font-semibold text-amber-300">What happens next</p>
                <p className="mt-2 text-sm leading-6 text-slate-300">
                  You will receive confirmation details, event logistics, and reminders for the forum on 23rd April, 2026 by 11:00 AM at Ibadan Business School, Francis Okediji Street, off Adeyi Avenue, Old Bodija, Ibadan.
                </p>
              </div>
              <div className="rounded-2xl border border-white/10 bg-black/20 p-5">
                <p className="text-sm font-semibold text-amber-300">Why this matters</p>
                <p className="mt-2 text-sm leading-6 text-slate-300">
                  Your responses help us understand your diesel pain points so the forum can be commercially useful, not just informational.
                </p>
              </div>
            </div>
            <div className="mt-8 flex flex-col items-center justify-center gap-3 sm:flex-row">
              <a
                href={calendarUrl}
                target="_blank"
                rel="noreferrer"
                className="inline-flex items-center justify-center rounded-2xl bg-white px-5 py-3 font-semibold text-slate-900 transition hover:translate-y-[-1px]"
              >
                Add to Calendar
              </a>
              <a
                href={whatsappUrl}
                target="_blank"
                rel="noreferrer"
                className="inline-flex items-center justify-center rounded-2xl border border-white/15 bg-white/5 px-5 py-3 font-semibold text-white transition hover:translate-y-[-1px]"
              >
                Contact on WhatsApp
              </a>
              <button
                onClick={() => setSubmitted(false)}
                className="rounded-2xl border border-white/15 bg-white px-5 py-3 font-semibold text-slate-900 transition hover:translate-y-[-1px]"
              >
                Submit another response
              </button>
            </div>
          </div>
        </div>
      </div>
    );
  }

  return (
    <div className="min-h-screen bg-[radial-gradient(circle_at_top,_rgba(250,204,21,0.15),_transparent_28%),linear-gradient(to_bottom,_#ffffff,_#f8fafc)] text-slate-900">
      <section className="mx-auto max-w-7xl px-6 py-8 lg:px-12 lg:py-12">
        <div className="grid items-start gap-8 lg:grid-cols-[1.05fr_0.95fr] xl:gap-12">
          <div className="lg:sticky lg:top-8">
            <div className="inline-flex rounded-full border border-amber-300 bg-amber-50 px-4 py-1.5 text-sm font-semibold text-amber-700">
              Gas Transitioning Forum 2026
            </div>

            <h1 className="mt-6 max-w-3xl text-4xl font-bold leading-tight tracking-tight sm:text-5xl xl:text-6xl">
              Diesel is draining your margins. Discover how gas can cut energy costs and power business growth.
            </h1>

            <p className="mt-6 max-w-2xl text-lg leading-8 text-slate-600">
              This forum is for serious business owners and operators who want a practical path away from diesel dependence. Meet generator suppliers, gas suppliers, storage partners, logistics operators, and financing players in one deal-focused environment.
            </p>

            <div className="mt-6 grid gap-4 sm:grid-cols-3">
              <div className="rounded-[22px] border border-slate-200 bg-white p-4 shadow-sm">
                <p className="text-xs font-semibold uppercase tracking-[0.16em] text-slate-500">Date</p>
                <p className="mt-2 text-base font-semibold leading-6 text-slate-900">23rd April, 2026</p>
              </div>
              <div className="rounded-[22px] border border-slate-200 bg-white p-4 shadow-sm">
                <p className="text-xs font-semibold uppercase tracking-[0.16em] text-slate-500">Time</p>
                <p className="mt-2 text-base font-semibold leading-6 text-slate-900">11:00 AM prompt</p>
              </div>
              <div className="rounded-[22px] border border-slate-200 bg-white p-4 shadow-sm sm:col-span-3 lg:col-span-1">
                <p className="text-xs font-semibold uppercase tracking-[0.16em] text-slate-500">Venue</p>
                <p className="mt-2 text-base font-semibold leading-6 text-slate-900">Ibadan Business School</p>
                <p className="mt-1 text-sm leading-6 text-slate-600">Francis Okediji Street, off Adeyi Avenue, Old Bodija, Ibadan</p>
              </div>
            </div>

            <div className="mt-6 flex flex-col gap-3 sm:flex-row">
              <a
                href={calendarUrl}
                target="_blank"
                rel="noreferrer"
                className="inline-flex items-center justify-center rounded-2xl bg-slate-900 px-5 py-3 text-sm font-semibold text-white shadow-lg transition hover:translate-y-[-1px]"
              >
                Add to Calendar
              </a>
              <a
                href={whatsappUrl}
                target="_blank"
                rel="noreferrer"
                className="inline-flex items-center justify-center rounded-2xl border border-slate-300 bg-white px-5 py-3 text-sm font-semibold text-slate-900 transition hover:border-slate-400 hover:translate-y-[-1px]"
              >
                Contact on WhatsApp
              </a>
            </div>

            <div className="mt-8 grid gap-4 sm:grid-cols-2">
              <div className="rounded-[24px] border border-slate-200 bg-white p-5 shadow-sm">
                <p className="text-sm font-semibold uppercase tracking-wide text-slate-500">What you gain</p>
                <p className="mt-2 text-base font-medium leading-7 text-slate-800">
                  Clear transition options, real savings insight, access to solution providers, and commercial conversations that can move immediately after the event.
                </p>
              </div>
              <div className="rounded-[24px] border border-slate-200 bg-white p-5 shadow-sm">
                <p className="text-sm font-semibold uppercase tracking-wide text-slate-500">Who should attend</p>
                <p className="mt-2 text-base font-medium leading-7 text-slate-800">
                  Factories, hotels, hospitals, schools, estates, commercial facilities, processors, and any business carrying heavy diesel power costs.
                </p>
              </div>
            </div>

            <div className="mt-8 rounded-[28px] border border-slate-200 bg-slate-900 p-6 text-white shadow-xl">
              <p className="text-sm font-semibold uppercase tracking-[0.16em] text-amber-300">Why register now</p>
              <h2 className="mt-3 text-2xl font-bold">This is not just an event sign-up. It is a lead qualification page.</h2>
              <p className="mt-3 text-base leading-7 text-slate-300">
                We are collecting real operating data so we can understand your diesel pain points, identify likely-fit businesses, and prioritize meaningful follow-up after the forum.
              </p>
              <div className="mt-6 grid gap-3 text-sm text-slate-200 sm:grid-cols-2">
                <div className="rounded-2xl border border-white/10 bg-white/5 px-4 py-3">Capture high-intent business leads</div>
                <div className="rounded-2xl border border-white/10 bg-white/5 px-4 py-3">Segment prospects by energy need</div>
                <div className="rounded-2xl border border-white/10 bg-white/5 px-4 py-3">Understand spend and urgency</div>
                <div className="rounded-2xl border border-white/10 bg-white/5 px-4 py-3">Book post-event consultations</div>
              </div>
            </div>
          </div>

          <div className="rounded-[32px] border border-slate-200 bg-white p-6 shadow-2xl sm:p-8">
            <div className="mb-6 border-b border-slate-100 pb-6">
              <p className="text-sm font-semibold uppercase tracking-[0.16em] text-amber-700">Reserve your seat</p>
              <h2 className="mt-2 text-3xl font-bold tracking-tight">Tell us about your business power reality.</h2>
              <p className="mt-3 text-sm leading-6 text-slate-600">
                Complete this short form so we can prepare relevant conversations for the forum and contact you with event details. The event holds on <span className="font-semibold text-slate-900">23rd April, 2026</span> at <span className="font-semibold text-slate-900">11:00 AM prompt</span>, at <span className="font-semibold text-slate-900">Ibadan Business School, Francis Okediji Street, off Adeyi Avenue, Old Bodija, Ibadan</span>.
              </p>
            </div>

            <form className="space-y-8" onSubmit={handleSubmit}>
              <div>
                <p className="mb-4 text-sm font-semibold uppercase tracking-wide text-slate-500">1. Contact information</p>
                <div className="grid gap-5 sm:grid-cols-2">
                  <div>
                    <label className="mb-2 block text-sm font-medium text-slate-700">Full Name</label>
                    <input
                      type="text"
                      required
                      value={formData.fullName}
                      onChange={(e) => handleChange("fullName", e.target.value)}
                      placeholder="Your full name"
                      className="w-full rounded-2xl border border-slate-300 px-4 py-3 outline-none transition focus:border-slate-900"
                    />
                  </div>
                  <div>
                    <label className="mb-2 block text-sm font-medium text-slate-700">Phone Number</label>
                    <input
                      type="tel"
                      required
                      value={formData.phone}
                      onChange={(e) => handleChange("phone", e.target.value)}
                      placeholder="e.g. 0800 000 0000"
                      className="w-full rounded-2xl border border-slate-300 px-4 py-3 outline-none transition focus:border-slate-900"
                    />
                  </div>
                  <div>
                    <label className="mb-2 block text-sm font-medium text-slate-700">Email Address</label>
                    <input
                      type="email"
                      required
                      value={formData.email}
                      onChange={(e) => handleChange("email", e.target.value)}
                      placeholder="you@company.com"
                      className="w-full rounded-2xl border border-slate-300 px-4 py-3 outline-none transition focus:border-slate-900"
                    />
                  </div>
                  <div>
                    <label className="mb-2 block text-sm font-medium text-slate-700">Job Title</label>
                    <input
                      type="text"
                      value={formData.jobTitle}
                      onChange={(e) => handleChange("jobTitle", e.target.value)}
                      placeholder="e.g. CEO, Operations Manager"
                      className="w-full rounded-2xl border border-slate-300 px-4 py-3 outline-none transition focus:border-slate-900"
                    />
                  </div>
                </div>
              </div>

              <div>
                <p className="mb-4 text-sm font-semibold uppercase tracking-wide text-slate-500">2. Business information</p>
                <div className="grid gap-5 sm:grid-cols-2">
                  <div>
                    <label className="mb-2 block text-sm font-medium text-slate-700">Business Name</label>
                    <input
                      type="text"
                      required
                      value={formData.businessName}
                      onChange={(e) => handleChange("businessName", e.target.value)}
                      placeholder="Your company name"
                      className="w-full rounded-2xl border border-slate-300 px-4 py-3 outline-none transition focus:border-slate-900"
                    />
                  </div>
                  <div>
                    <label className="mb-2 block text-sm font-medium text-slate-700">Industry</label>
                    <select
                      required
                      value={formData.industry}
                      onChange={(e) => handleChange("industry", e.target.value)}
                      className="w-full rounded-2xl border border-slate-300 bg-white px-4 py-3 outline-none transition focus:border-slate-900"
                    >
                      <option value="">Select industry</option>
                      <option>Manufacturing</option>
                      <option>Hospitality</option>
                      <option>Healthcare</option>
                      <option>Education</option>
                      <option>Estate Management</option>
                      <option>Retail / Commercial</option>
                      <option>Agro Processing</option>
                      <option>Logistics / Warehousing</option>
                      <option>Other</option>
                    </select>
                  </div>
                  <div>
                    <label className="mb-2 block text-sm font-medium text-slate-700">Business Location</label>
                    <input
                      type="text"
                      required
                      value={formData.location}
                      onChange={(e) => handleChange("location", e.target.value)}
                      placeholder="City / State"
                      className="w-full rounded-2xl border border-slate-300 px-4 py-3 outline-none transition focus:border-slate-900"
                    />
                  </div>
                  <div>
                    <label className="mb-2 block text-sm font-medium text-slate-700">Are you a decision maker?</label>
                    <select
                      required
                      value={formData.decisionMaker}
                      onChange={(e) => handleChange("decisionMaker", e.target.value)}
                      className="w-full rounded-2xl border border-slate-300 bg-white px-4 py-3 outline-none transition focus:border-slate-900"
                    >
                      <option value="">Select option</option>
                      <option>Yes</option>
                      <option>Part of the decision team</option>
                      <option>No</option>
                    </select>
                  </div>
                </div>
              </div>

              <div>
                <p className="mb-4 text-sm font-semibold uppercase tracking-wide text-slate-500">3. Diesel usage and cost profile</p>
                <div className="grid gap-5 sm:grid-cols-2">
                  <div>
                    <label className="mb-2 block text-sm font-medium text-slate-700">Estimated Generator Size</label>
                    <select
                      required
                      value={formData.generatorSize}
                      onChange={(e) => handleChange("generatorSize", e.target.value)}
                      className="w-full rounded-2xl border border-slate-300 bg-white px-4 py-3 outline-none transition focus:border-slate-900"
                    >
                      <option value="">Select range</option>
                      <option>Below 50 kVA</option>
                      <option>50 - 100 kVA</option>
                      <option>100 - 250 kVA</option>
                      <option>250 - 500 kVA</option>
                      <option>500 kVA and above</option>
                      <option>Not sure</option>
                    </select>
                  </div>
                  <div>
                    <label className="mb-2 block text-sm font-medium text-slate-700">Number of Generators</label>
                    <select
                      value={formData.generatorCount}
                      onChange={(e) => handleChange("generatorCount", e.target.value)}
                      className="w-full rounded-2xl border border-slate-300 bg-white px-4 py-3 outline-none transition focus:border-slate-900"
                    >
                      <option value="">Select option</option>
                      <option>1</option>
                      <option>2 - 3</option>
                      <option>4 - 6</option>
                      <option>More than 6</option>
                    </select>
                  </div>
                  <div>
                    <label className="mb-2 block text-sm font-medium text-slate-700">How often do you rely on diesel generators?</label>
                    <select
                      required
                      value={formData.usageFrequency}
                      onChange={(e) => handleChange("usageFrequency", e.target.value)}
                      className="w-full rounded-2xl border border-slate-300 bg-white px-4 py-3 outline-none transition focus:border-slate-900"
                    >
                      <option value="">Select an option</option>
                      <option>Daily</option>
                      <option>Several times a week</option>
                      <option>Occasionally</option>
                      <option>Only as backup</option>
                    </select>
                  </div>
                  <div>
                    <label className="mb-2 block text-sm font-medium text-slate-700">Average hours of use per day</label>
                    <select
                      value={formData.hoursPerDay}
                      onChange={(e) => handleChange("hoursPerDay", e.target.value)}
                      className="w-full rounded-2xl border border-slate-300 bg-white px-4 py-3 outline-none transition focus:border-slate-900"
                    >
                      <option value="">Select range</option>
                      <option>1 - 4 hours</option>
                      <option>5 - 8 hours</option>
                      <option>9 - 12 hours</option>
                      <option>13 - 18 hours</option>
                      <option>19 - 24 hours</option>
                    </select>
                  </div>
                  <div className="sm:col-span-2">
                    <label className="mb-2 block text-sm font-medium text-slate-700">Estimated monthly diesel spend</label>
                    <select
                      required
                      value={formData.monthlyDieselSpend}
                      onChange={(e) => handleChange("monthlyDieselSpend", e.target.value)}
                      className="w-full rounded-2xl border border-slate-300 bg-white px-4 py-3 outline-none transition focus:border-slate-900"
                    >
                      <option value="">Select spend range</option>
                      <option>Below ₦500,000</option>
                      <option>₦500,000 - ₦1,000,000</option>
                      <option>₦1,000,000 - ₦3,000,000</option>
                      <option>₦3,000,000 - ₦5,000,000</option>
                      <option>Above ₦5,000,000</option>
                      <option>Prefer not to say</option>
                    </select>
                  </div>
                </div>
              </div>

              <div>
                <p className="mb-4 text-sm font-semibold uppercase tracking-wide text-slate-500">4. Pain points and intent</p>
                <div>
                  <label className="mb-3 block text-sm font-medium text-slate-700">What are your biggest diesel-related pain points?</label>
                  <div className="grid gap-3 sm:grid-cols-2">
                    {painPointOptions.map((item) => (
                      <label
                        key={item}
                        className="flex items-center gap-3 rounded-2xl border border-slate-200 px-4 py-3 text-sm text-slate-700 transition hover:border-slate-300"
                      >
                        <input
                          type="checkbox"
                          checked={formData.painPoints.includes(item)}
                          onChange={() => handleCheckbox(item)}
                          className="h-4 w-4 rounded border-slate-300"
                        />
                        <span>{item}</span>
                      </label>
                    ))}
                  </div>
                </div>

                <div className="mt-5 grid gap-5 sm:grid-cols-2">
                  <div>
                    <label className="mb-2 block text-sm font-medium text-slate-700">When are you looking to transition?</label>
                    <select
                      required
                      value={formData.transitionTimeline}
                      onChange={(e) => handleChange("transitionTimeline", e.target.value)}
                      className="w-full rounded-2xl border border-slate-300 bg-white px-4 py-3 outline-none transition focus:border-slate-900"
                    >
                      <option value="">Select timeline</option>
                      <option>Immediately</option>
                      <option>Within 3 months</option>
                      <option>Within 6 months</option>
                      <option>Just exploring for now</option>
                    </select>
                  </div>
                  <div>
                    <label className="mb-2 block text-sm font-medium text-slate-700">Would you like a post-event consultation?</label>
                    <select
                      required
                      value={formData.consultation}
                      onChange={(e) => handleChange("consultation", e.target.value)}
                      className="w-full rounded-2xl border border-slate-300 bg-white px-4 py-3 outline-none transition focus:border-slate-900"
                    >
                      <option value="">Select option</option>
                      <option>Yes</option>
                      <option>Maybe</option>
                      <option>No</option>
                    </select>
                  </div>
                </div>

                <div className="mt-5">
                  <label className="mb-2 block text-sm font-medium text-slate-700">Tell us briefly about your current diesel challenges</label>
                  <textarea
                    rows={5}
                    value={formData.challenges}
                    onChange={(e) => handleChange("challenges", e.target.value)}
                    placeholder="Share your biggest fuel cost concerns, maintenance burden, downtime issues, or any specific questions you want addressed at the forum."
                    className="w-full rounded-2xl border border-slate-300 px-4 py-3 outline-none transition focus:border-slate-900"
                  />
                </div>
              </div>

              <div className="rounded-[24px] border border-amber-200 bg-amber-50 p-5">
                <p className="text-sm font-semibold text-amber-800">Submission flow</p>
                <p className="mt-2 text-sm leading-6 text-slate-700">
                  On submit, this form is structured to send the registrant data to a CRM, Airtable, Google Sheet, or webhook endpoint. The fields are designed to support lead capture, qualification, segmentation, and post-event follow-up.
                </p>
              </div>

              <button
                type="submit"
                className="w-full rounded-2xl bg-slate-900 px-5 py-4 text-base font-semibold text-white shadow-lg transition hover:translate-y-[-1px]"
              >
                Reserve My Seat
              </button>

              <p className="text-center text-xs leading-5 text-slate-500">
                By submitting this form, you agree to be contacted about the forum, registration updates, and relevant gas transition opportunities for your business.
              </p>
            </form>
          </div>
        </div>
      </section>
    </div>
  );
}
